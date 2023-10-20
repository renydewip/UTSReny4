# UTSReny4
DISCLAIMER
Mohon maaf pak sebelumnya jika jika user commite yang saya gunakan berbeda dikarenakan saya 
menggunakan laptop teman saya dikarenakan laptop saya tidak kuat untuk menjalankan program 
Android studio

Laporan Ujian Tengah Semester 

!. Syntax 1

class MainActivity : ComponentActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContent {
            UTSReny4Theme {

                Surface(
                    modifier = Modifier.fillMaxSize(),

                ) {
                    MainMenu()
                }
            }
        }
    }
}

source code dibawah ini berfungsi untuk memberi definisi dari kelas MainActivity yang merupakan aktivitas utama dalam aplikasi. 
aktivitas ini dibuat, metode onCreate akan dipanggil dan berfungsi untuk mengatur tampilan aktivitas menggunakan framework UI yang 
disebut "Jetpack Compose." Tampilan utama ini dibangun dengan menggunakan komponen Surface yang mengisi seluruh layar dan menampilkan 
konten dari MainMenu.Selain itu, kode ini juga menggunakan tema yang disebut UTSReny4Theme untuk mengatur gaya dan tampilan 
keseluruhan aplikasi.

2 Syntax 2

@Composable
fun MainMenu(){
   
    var currentImage by remember { mutableStateOf(1) }
    Surface(
        modifier = Modifier.fillMaxSize())
    {
        when(currentImage){
            1 -> {
                MainMenuImage(
                    imageResource =R.drawable.zulhas,
                    nameResource = R.string.L1,
                    authorResource = R.string.Creator,
                    onNextButtonClick = { currentImage = 2 },
                    onPreviousButtonClick = { currentImage = 4 },
                )
            }
            2 -> {
                MainMenuImage(
                    imageResource = R.drawable.israel,
                    nameResource = R.string.L2,
                    authorResource = R.string.Creator,
                    onNextButtonClick = { currentImage = 3 },
                    onPreviousButtonClick = { currentImage = 1 })
            }
            3 -> {
                MainMenuImage(
                    imageResource = R.drawable.mario,
                    nameResource = R.string.L3,
                    authorResource = R.string.Creator,
                    onNextButtonClick = { currentImage = 4 },
                    onPreviousButtonClick = { currentImage = 2 })
            }
            4 -> {
                MainMenuImage(
                    imageResource = R.drawable.demo,
                    nameResource = R.string.L4,
                    authorResource = R.string.Creator,
                    onNextButtonClick = { currentImage = 1},
                    onPreviousButtonClick = { currentImage = 3 })
            }
        }
    }
}
Potongan source code diatas adalah fungsi MainMenu yang menggunakan Compose. Fungsi ini membangun tampilan utama dalam layar. 
Pada fungsi ini, terdapat variabel currentImage yang digunakan untuk mengontrol gambar yang ditampilkan.Pertama, fungsi ini mengatur 
tampilan Surface agar mengisi seluruh layar.Kemudian, terdapat blok when yang bergantung pada nilai currentImage. Terdapat empat kondisi yang berbeda, 
masing-masing menampilkan gambar berbeda dengan detail seperti judul dan pengarang.Setiap kondisi dalam blok when menggunakan komponen MainMenuImage dengan parameter berbeda, 
seperti imageResource, nameResource, dan authorResource yang mengacu pada sumber daya gambar, judul, dan pengarang gambar.Ketika pengguna menekan tombol "Next" atau "Previous"
pada tampilan gambar, currentImage akan diubah untuk memperbarui tampilan sesuai dengan gambar berikutnya atau sebelumnya, tergantung pada kondisi saat ini.

3.Syntax 3

@Composable

fun MainMenuImage(
   
    imageResource: Int,
    nameResource: Int,
    authorResource: Int,
    onNextButtonClick: () -> Unit,
    onPreviousButtonClick: () -> Unit,
    modifier: Modifier = Modifier
)
{
   
    Box(modifier = Modifier.fillMaxSize()) {
        Column(
            horizontalAlignment = Alignment.CenterHorizontally,
            verticalArrangement = Arrangement.Center,
            modifier = modifier.fillMaxSize()
        ) {
            Surface(
                border = BorderStroke(3.dp, color = Color.LightGray)
            ) {
                Image(
                    painter = painterResource(imageResource),
                    contentDescription = null,
                    modifier = Modifier.padding(32.dp)
                )
            }
            Spacer(modifier = Modifier.height(8.dp))
            Surface(
                modifier = Modifier
                    .align(Alignment.CenterHorizontally)
                    .padding(30.dp, 16.dp)
            ) {
                Column {
                    Text(
                        text = stringResource(nameResource),
                        modifier = Modifier
                            .padding(16.dp, 16.dp, 16.dp, 0.dp),
                        fontSize = 22.sp
                    )
                    Text(
                        text = stringResource(authorResource),
                        modifier = Modifier.padding(16.dp, 0.dp, 16.dp, 16.dp),
                        fontWeight = FontWeight.Bold,
                        fontSize = 12.sp
                    )
                }
            }
        }
        Surface(
            modifier = Modifier
                .align(Alignment.BottomCenter)
                .padding(30.dp, 16.dp)
        ) {
            Row(
                modifier = Modifier.fillMaxWidth(),
                horizontalArrangement = Arrangement.SpaceBetween
            ) {
                CustomButton(
                    onClick = { onPreviousButtonClick() },
                    modifier = Modifier.padding(8.dp),
                    text = stringResource(R.string.previous)
                )
                CustomButton(
                    onClick = { onNextButtonClick() },
                    modifier = Modifier.padding(8.dp),
                    text = stringResource(R.string.next)
                )
            }
        }
    }
}

Potongan source code dengan nama MainMenuImage yang merupakan komponen Composable dalam aplikasi Android. Fungsi ini bertujuan untuk
membangun tampilan gambar dengan detail yang terdiri dari gambar itu sendiri, judul, pengarang, dan tombol "Previous" dan "Next". 
Berikut adalah penjelasan singkat dari Fungsi MainMenuImage menerima berbagai parameter, seperti imageResource (gambar yang akan ditampilkan), 
nameResource (judul gambar), authorResource (pengarang gambar), serta fungsi onNextButtonClick dan onPreviousButtonClick yang akan dipanggil saat tombol "Next" atau "Previous" ditekan.
Fungsi ini membangun tampilan menggunakan komponen Composable, termasuk Box, Column, Surface, Image, Text, dan CustomButton. 
Gambar ditampilkan di tengah dengan judul dan pengarang di bawahnya. Di bagian bawah gambar terdapat tombol "Previous" dan "Next" untuk mengganti gambar yang ditampilkan.
Beberapa modifikasi juga diterapkan menggunakan Modifier untuk mengatur tata letak, margin, dan tampilan komponen-komponen tersebut.Tampilan ini dikomposisikan secara 
hierarkis dan diberikan ke Box, yang mengisi seluruh layar dengan elemen-elemen yang ditempatkan di dalamnya

4.Syntax 4
@Composable
fun CustomButton(
    
    onClick: () -> Unit,
    modifier: Modifier,
    text: String
) 
{
    
    Button(
        onClick = { onClick() },
        modifier = modifier
    ) {
        Text(text = text, Modifier.padding(12.dp, 0.dp))
    }
}

@Preview(showBackground = true)
@Composable
fun DefaultPreview() {
    
    UTSReny4Theme {
        MainMenu()
    }
}
CustomButton memiliki fungsi komponen Composable yang digunakan untuk membuat tombol kustom. Fungsi ini menerima tiga parameter: onClick (tindakan yang akan dijalankan saat tombol diklik),
modifier (modifikasi tampilan tombol), dan text (teks yang akan ditampilkan pada tombol). Fungsi ini mengandung sebuah Button yang akan mengeksekusi onClick saat tombol diklik, 
dan menampilkan teks pada tombol. DefaultPreview: Ini adalah fungsi komponen Composable yang digunakan untuk menampilkan tampilan awal atau pratinjau dari aplikasi 
Fungsi ini menggambarkan tampilan utama menggunakan tema  UTSReny4Theme dan menampilkan MainMenu sebagai konten awal yang akan ditampilkan dalam pratinjau aplikasi.
