# FARKLI AKTİVİTELER ARASINDA GEÇİŞ (VİEW BİNDİNG)

Merhabalar bu yazımda size farklı aktiviteler arasında nasıl geçiş yapılır bunu göstereceğim bunun için anlattığım şeylerin daha anlaşılır olması için ise örnek bir uygulama tasarlayacağız örnek uygulama bize bu konuyu daha iyi anlamamızı sağlayacak. İlk medium yazımı bu konu hakkında yazmak istedim umarım anlaşılır olmuştur. Şimdi uygulamamızı yazmaya başlayalım;
Proje ile ilgili gerekli kod ve tasarım görsellerini GitHub profilime ekliyorum aşağıda ki linkten ulaşabilirsiniz.


1.BÖLÜM

İlk olarak boş bir aktivite oluşturmamız gerekiyor. Bunun için Android Studio’yu açalım;
Ardından New diyelim ve yeni Activity Oluşturmak için Empty Activity seçeneğini seçelim;
Bir sonra ki adımda uygulamaya ismimizi girmemiz gerekiyor burada istediğiniz ismi verebilirsiniz. Ben First Activity ismini verdim ve boş aktivitemi açtım.
Oluşturduğumuz aktivite içerisinde Gradle Scripts kısmından build.gradle(Module) kısmını açıyoruz ve açtığımız kısımda android starının altına aşağıda ki kodu ekliyoruz ve Sync Now diyerek kodumuzu aktif ve çalışır duruma getiriyoruz.
Kodumuz;

}
buildFeatures {
viewBinding true
}


Peki bu kod ne işe yarıyor?
Bu kod görünümleri bağlamayı ve aktif etmek için kullanılır. Bu kadı aktif hale getirdiğimiz taktirde yazdığımız Kotlin kotları çalışır hale gelmektedir.




2.BÖLÜM

Canva üzerinden tasarladığım üç adet arka plan görselini Android Studio içerisine aktaralım. Oluşturduğumuz tasarım görsellerinin tümünü seçelim ve Ctrl-C yapalım ardından Android Studio içerisinde ki drawable kısmına tıklayıp Ctrl-V yaparız burada dikkat etmemiz gereken kısım tasarımları drawable kısmı. Burada bize iki farklı yükleme alanı seçeneği sunulur bunlardan biri drawable-24 diğeri drawable biz drawable’ı seçerek uygulamaya devam ederiz.
MainActivity İçin Tasarımların ve Uygulama İçeriğinin Oluşturulması;

1.Arkaplan Tasarımının Eklenmesi
İlk olarak Activity_main.xml kısmına geliyoruz ve buradan Constraintlayout içerisine İmageView atıyoruz. Bu atadığımız İmageView bizim drawable kısmına yüklediğimiz tasarım görsellerinden biri olacak. Daha sonra tasarıma uygun olsun diye bir background kodu ekleyelim ben tasarımımla aynı renk kodu ekledim siz farklı bir kod ekleyebilirsiniz;
android:background="#009FBF"

2.TextView Eklenmesi
Daha sonra tasarım üzerine bir TextView atıyoruz. Bu TextView içerisine ben “Bir Sonra ki Sayfaya Gitmek İçin Tıklayın” yazdım siz farklı bir şey isterseniz yazabilirsiniz.
Ben TextView özelliklerini activity_main.xml kısmının Code/Spilit alanından xml kodları ile yapıyorum. Siz design kısmından da yapabilirsiniz. Aşağıda TextView kodunu ekliyorum;

<TextView

android:id="@+id/textView"

android:layout_width="266dp"

android:layout_height="105dp"

android:layout_marginStart="80dp"

android:layout_marginTop="396dp"

android:text="@string/bir_sonra_ki_sayfaya_ge_mek_in_t_klay_n"

android:textAlignment="center"

android:textSize="15sp"

android:textStyle="bold"

app:layout_constraintStart_toStartOf="parent"

app:layout_constraintTop_toTopOf="@+id/imageView2" />

3.Button Eklenmesi
Burada TextView altına bir buton ekliyoruz ve Button içerisine istediğinizi yazabilirsiniz. Ben “Tıklayın” yazdım ve aşağıya Button kodunu ekliyorum;

<Button

android:id="@+id/button"

android:layout_width="wrap_content"

android:layout_height="wrap_content"

android:layout_marginTop="80dp"

android:text="@string/t_klay_n"

app:layout_constraintBottom_toBottomOf="@+id/imageView2"

app:layout_constraintEnd_toEndOf="parent"

app:layout_constraintStart_toStartOf="parent"

app:layout_constraintTop_toBottomOf="@id/textView" />


Bu kısım için yapacaklarımız bu kadar tasarımlarımız ilk kısım için tamamladık şimdi sıra MainActivity.kt bölümün de kodlarımızı düzenlemeye
MainActivity.kt İçinde Kodların Yazılması;
Bu kısma başlamadan önce New kısmından yeni bir Empty Activity oluşturalım bu oluşturduğumuz aktiviteye SecondActivity diyelim bu sayfa bizim uygulamamızın ikinci kısmı olacak.

Kodumuzu yazmaya başlayalım;

class MainActivity : AppCompatActivity() {

Bu kodun altına yeni bir kod ekliyoruz;

private lateinit var binding: ActivityMainBinding

Bu kodu yazarak viewlara erişim sağlamak için bir öğe oluşturmuş oluruz.
Daha sonra onCreate altına binding’imizin tanıtımını yapmak için aşağıda ki kodu ekliyoruz;

binding = ActivityMainBinding.inflate(layoutInflater)

Ardından burada bulanan;

setContentView(R.layout.activity_main)

Bu kod üzerinde düzenleme yaparak;

setContentView(binding.root)

Olarak değiştiriyoruz bu da bize viewları döndürmüş olur.
Mevcut butonumuza bir rol eklemek için bir kod yazmamız gerekiyor. Bu kodu intent yapısını kullanarak yazıyoruz, İntent yapısı başka bir aktivitenin çalıştırılması için kullanılır.

binding.button.setOnClickListener {

val intent = Intent (this, SecondActivity :: class.java)

startActivity(intent)
Burada SecondActivity kısmı bizim kodumuzu yazmaya başlamadan önce açtığımız kısım yani ikinci sayfamız olur. Bu bölüm burada tamamlanır ve MainActivity kısmı SecondActivity ile bağlanmış olur.


3.BÖLÜM

2.BÖLÜM de yapılan tasarım aşamalarının aynılarını SecondActivity için de yapalım. Ben sadece burada TextView ve Button kodlarını yardımcı olması için paylaşacağım;

TextView;

<TextView

android:id="@+id/textView2"

android:layout_width="wrap_content"

android:layout_height="wrap_content"

android:layout_marginStart="72dp"

android:layout_marginTop="460dp"

android:text="@string/bir_sonra_ki_sayfaya_gitmek_ster_misiniz"

android:textStyle="bold"

android:textSize="15sp"

app:layout_constraintEnd_toEndOf="parent"

app:layout_constraintHorizontal_bias="0.038"

app:layout_constraintStart_toStartOf="@id/imageView"

app:layout_constraintTop_toTopOf="@+id/imageView" />

2.Button;

<Button

android:id="@+id/button2"

android:layout_width="wrap_content"

android:layout_height="wrap_content"

android:layout_marginStart="88dp"

android:layout_marginTop="61dp"

android:layout_marginEnd="124dp"

android:text="@string/evet"

app:layout_constraintBottom_toBottomOf="@+id/imageView"

app:layout_constraintEnd_toEndOf="@+id/imageView"

app:layout_constraintStart_toStartOf="@id/textView2"

app:layout_constraintTop_toBottomOf="@+id/textView2" />

SecondActivity.kt İçinde Kodların Yazılması;

Burada MainActivity.kt kısmı için yazdığımız kodların aynısını yazıyoruz. Fakat burada farklı bir activity içerisinde çalıştığımız için o aktiviteye göre kodlarımızı düzenlememiz gerekiyor. Buradan SecondActivity.kt içerisinde ki kodlarımız;

class SecondActivity : AppCompatActivity() {

private lateinit var binding: ActivitySecondBinding

override fun onCreate(savedInstanceState: Bundle?) {

super.onCreate(savedInstanceState)

binding = ActivitySecondBinding.inflate(layoutInflater)

setContentView(binding.root)

binding.button2.setOnClickListener {

val intent = Intent (this, ThirdActivity::class.java)

startActivity(intent)

}
Burada da gördüğünüz gibi ThirdActivity bizim bir sonra ki açılacak olan aktivitemizin sınıfı bu kodu yazmadan önce New kısmından Empty Activity açmamız gerekiyor ve bu bizim ThirdActivity’miz olur.



4.BÖLÜM


Yine aynı tasarım işlemlerini ThirdActivity için de yapıyoruz. Bu kısımda da aynı şekilde bir TextView ve bir Button ekliyoruz. Aşağıya kodlarını ekliyorum;


TextView;

<TextView

android:id="@+id/textView3"

android:layout_width="wrap_content"

android:layout_height="wrap_content"

android:layout_marginTop="416dp"

android:text="@string/anasayfaya_d_nemek_ster_misiniz"

android:textSize="17sp"

android:textStyle="bold"

app:layout_constraintEnd_toEndOf="parent"

app:layout_constraintStart_toStartOf="parent"

app:layout_constraintTop_toTopOf="@+id/imageView3" />

2.Button;

<Button

android:id="@+id/button3"

android:layout_width="wrap_content"

android:layout_height="wrap_content"

android:layout_marginTop="40dp"

app:layout_constraintBottom_toBottomOf="parent"

app:layout_constraintEnd_toEndOf="parent"

app:layout_constraintStart_toStartOf="parent"

app:layout_constraintTop_toBottomOf="@id/textView3"

android:text="@string/st_yorum"

android:textStyle="bold" />

ThirdActivity.kt İçinde Kodların Yazılması;

Bu kısım uygulamamızın son sayfası olacak ve bizi uygulamamız ilk açıldığında açılacak olan sayfaya geri yollayacak. Bunun için de değişiklik yapılacak ilk iki aktivite için yaptığımız işlemler aynı olacağından aşağıya yazdığımız kodu ekliyorum;

class ThirdActivity : AppCompatActivity() {

private lateinit var binding: ActivityThirdBinding

override fun onCreate(savedInstanceState: Bundle?) {

super.onCreate(savedInstanceState)

binding = ActivityThirdBinding.inflate(layoutInflater)

setContentView(binding.root)

binding.button3.setOnClickListener {

val intent = Intent (this, MainActivity::class.java)

startActivity(intent)


KAYNAK
GitHub : https://github.com/srdrakcay/ViewBinding
https://developer.android.com/topic/libraries/view-binding
