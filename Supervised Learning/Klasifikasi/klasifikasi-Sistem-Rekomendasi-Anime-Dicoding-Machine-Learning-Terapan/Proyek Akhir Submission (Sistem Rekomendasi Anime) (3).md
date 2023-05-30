
# Proyek Akhir Submission (Sistem Rekomendasi Anime)
Disusun oleh : Brilly Lutfan Qasthari
Laporan tentang hasil dokumentasi submission terakhir bertema Sistem Rekomendasi menggunakan *Content-based Filtering* dan *Collaborative Filtering*.
## Project Overview

Dalam beberapa tahun terakhir, anime telah menjadi fenomena global dan semakin populer di kalangan pecinta hiburan. Dengan peningkatan popularitas ini, jumlah anime yang bisa ditonton juga meningkat pesat. Namun, dengan banyaknya pilihan anime, pengguna seringkali kesulitan menemukan anime yang sesuai dengan minat dan preferensi mereka. Hal ini dapat membuat pengguna bingung, membuang waktu, bahkan frustasi dalam mencari anime yang diinginkan. 

Dalam konteks ini, sistem rekomendasi anime sangatlah penting. Sistem ini dapat membantu pengguna menemukan anime baru yang sesuai dengan minat, mengurangi kebingungan dalam memilih, dan memperluas wawasan anime. Dengan menggunakan teknik dan algoritma yang tepat, sistem rekomendasi anime dapat memberikan rekomendasi yang dipersonalisasi dan relevan kepada pengguna, sehingga meningkatkan pengalaman menonton dan kepuasan pengguna [[1](https://ojs.unud.ac.id/index.php/jnatia/article/download/92636/47032/)]. 

Sistem rekomendasi anime adalah sistem yang merekomendasikan anime kepada pengguna berdasarkan preferensi mereka. Sistem ini dapat membantu pengguna menemukan anime yang sesuai dengan selera. Latar belakang masalah yang dihadapi dalam pengembangan sistem rekomendasi anime adalah kurangnya kualitas informasi yang baik dan keterbatasan jumlah informasi [[2](https://repository.upnvj.ac.id/2016/1/AWAL.pdf)]. 

Oleh karena itu, pengembangan sistem rekomendasi anime sangat menarik untuk diteliti lebih lanjut. Sistem rekomendasi menawarkan berbagai manfaat yang dapat dicapai baik oleh pengguna maupun pengusaha. Oleh karena itu, sangat penting untuk dikembangkan lebih lanjut, terutama di saat informasi dan data berkembang dengan sangat cepat. Dalam proyek ini saya juga fokus pada pengembangan sistem rekomendasi anime. 

## Business Understanding

Dalam bisnis, sistem rekomendasi anime memiliki potensi besar untuk meningkatkan pengalaman pengguna, meningkatkan pangsa pasar, dan meningkatkan keterlibatan pengguna dalam industri anime. Berikut adalah beberapa aspek bisnis dari sistem rekomendasi anime seperti: 

1. **Personalisasi dan Pengalaman Pengguna yang Lebih Baik**
   Dengan menggunakan sistem rekomendasi anime, perusahaan dapat menawarkan pengalaman yang lebih personal dan relevan kepada pengguna. Dengan memahami preferensi pengguna, sistem dapat merekomendasikan anime berdasarkan minat mereka. Hal ini dapat meningkatkan kepuasan pengguna, meningkatkan waktu yang dihabiskan pengguna untuk menonton anime, dan meningkatkan loyalitas pengguna terhadap platform atau layanan yang memberikan rekomendasi tersebut.
2. **Meningkatkan Retensi Pengguna**
   Dalam industri yang penuh dengan pilihan anime, retensi pengguna menjadi faktor kunci kesuksesan bisnis. Sistem rekomendasi anime dapat membantu mempertahankan pengguna dengan terus memberikan rekomendasi yang relevan. Dengan mempertahankan pengguna yang ada, organisasi dapat meningkatkan nilai seumur hidup pengguna dan mengurangi churn. 
3. **Diversifikasi Penonton dan Mempengaruhi Pembelian**
   Sistem rekomendasi anime dapat membantu bisnis mengatasi tantangan dalam menjangkau audiens yang berbeda. Dengan menganalisis preferensi dan perilaku pengguna, sistem dapat merekomendasikan anime yang mungkin tidak diketahui pengguna atau yang berada di luar zona nyaman mereka. Ini dapat membantu perusahaan memperluas audiens mereka, memperkenalkan anime baru kepada pengguna, dan bahkan memengaruhi keputusan pembelian dalam bentuk pesanan barang dagangan, DVD, atau layanan streaming.

### Problem Statements

Berdasarkan masalah yang telah dijelaskan sebelumnya, masalah utama untuk proyek ini adalah sebagai berikut.
- Apakah sistem dapat memberikan rekomendasi yang relevan ?
- Bagaimana performa model dalam memprediksi rekomendasi untuk user ?

### Goals

Adapun tujuan yang dicapai oleh proyek ini sebagai berikut:
- Menghasilkan sebuha model sistem rekomendasi berbasis konten untuk memprediksi rekomendasi pengguna.
- Menghasilkan sebuha model sistem rekomendasi berbasis *collaborative filtering* untuk memprediksi rekomendasi pengguna.

### Solution statements

Adapun solusi yang dapat diberikan untuk proyek ini meliputi:
- Membuat sebuah sistem rekomendasi berbasis *Content-based Filtering* berdasarkan data genre anime.
- Membuat sebuah sistem rekomendasi berbasis *Collaborative Filtering* berdasarkan data rating anime yang telah diberikan oleh user.

## Data Understanding dan Preprocessing

Dataset yang digunakan dalam proyek ini adalah daftar judul anime dengan fitur, jumlah penggemar, dan rata-rata rating pengguna. Dataset dapat di unduh [disini](https://github.com/projekbrillylutfan/kumpulan_dataset/tree/main/Anime%20Dataset%20Rekomen), Kumpulan data ini berisi informasi data preferensi pengguna dari 73.516 pengguna di 12.294 anime. Setiap pengguna dapat menambahkan anime ke daftar lengkap mereka dan memberikannya peringkat dan kumpulan data ini adalah kompilasi dari peringkat tersebut.

variabel pada data `anime.csv` meliputi :
* `anime_id` = id unik untuk data ini.
* `name` = judul anime secara lengkap.
* `genre` = genre anime secara lengkap.
* `type` = tipe tayang anime.
* `episodes` = jumlah episode anime.
* `rating` = rata-rata rating anime.
* `members` = jumlah komunitas member di setiap anime.

variabel pada data `rating.csv` meliputi :
* `user_id ` = id unik untuk user.
* `anime_id ` = id untuk user yang telah voting.
* `rating ` = rentang rating dari 1 sampai 10.

### Data Preprocessing
1. menghapus simbol pada anime.
2. menghapus outlier pada data `anime.csv` dan `rating.csv`.
3. menghapus data duplikat.
4. menghapus data yang memiliki missing value.

### Univariate Analysis
Univariate Analysis adalah metode statistik yang digunakan untuk menganalisis satu variabel tunggal dalam suatu dataset. Tujuan dari analisis univariat adalah untuk memahami distribusi, pola, dan karakteristik dari variabel tersebut secara terpisah.
Tabel 1. Distribusi Anime csv
 | | anime_id | rating   | members |
|----------|----------|---------|---------|
| count    | 9922.00  | 9922.00 | 9922.00  |
| mean     | 13752.42 | 6.34    | 3259.68  |
| std      | 11213.94 | 0.87    | 5053.61  |
| min      | 8.00     | 3.96    | 17.00    |
| 25%      | 3517.25  | 5.79    | 178.00   |
| 50%      | 9884.50  | 6.42    | 959.50   |
| 75%      | 23907.50 | 6.95    | 3735.00  |
| max      | 34519.00 | 9.00    | 23631.00 |

Pada Tabel 1 dapat dilihat bahwa data anime memiliki rating anime terendah 1,67 dan rating tertinggi 10 dengan rata-rata 6,48. Dataset ini juga memiliki jumlah anggota komunitas anime terendah yaitu 12 dan tertinggi 1013917 dengan rata-rata 18348. Perbedaan jumlah minimum dan maksimum anggota komunitas anime cukup besar dan itu bisa dimaklumi karena beberapa anime sangat populer dan beberapa tidak.

Tabel 2. Distribusi rating csv

|  | user_id | anime_id   | rating     |
|---------|------------|------------|------------|
| count   | 6316305.00 | 6316305.00 | 6316305.00 |
| mean    | 36749.11   | 8888.00    | 7.83       |
| std     | 21014.12   | 8862.32    | 1.54       |
| min     | 1.00       | 1.00       | 2.00       |
| 25%     | 18978.00   | 1238.00    | 7.00       |
| 50%     | 36822.00   | 6211.00    | 8.00       |
| 75%     | 54873.00   | 14075.00   | 9.00       |
| max     | 73516.00   | 33372.00   | 10.00      |

Pada Tabel 2 menjelaskan bahwa Dalam catatan peringkat anime, peringkat terendah yang diberikan pengguna pada anime adalah -1 dan peringkat tertinggi adalah 10. Peringkat -1 berarti pengguna menonton anime tetapi tidak memberi peringkat. Pengguna sampel yang tidak memberikan peringkat tidak akan digunakan dan karenanya akan dihapus.

![Genre Terbanyak](https://i.ibb.co/m9dVbKM/genre.png)
Gambar 1. Visualisasi Genre Terbanyak

Pada Gambar 1 dapat dilihat kalau genre terbanyak ada di kategori hentai, kategori banyak kedua ada di genre komedi dan kategori terbanyak kedua ada di genre musik.

## Data Preparation
Pada tahapan ini saya melakukan:
1. Encoding kolom user id dan dan anime id yang bertujuan untuk mengubah data dari format yang asli menjadi format yang dapat dipahami atau diproses oleh komputer. Encoding adalah proses representasi data dengan menggunakan aturan tertentu agar dapat disimpan, ditransmisikan, atau diproses dengan efisien dan akurat. Dalam hal ini ada dua metode yang digunakan seperti kodingan di bawah:
    ```
    user_ids = df_train['user_id'].unique().tolist()
    user_to_user_encoded = {x: i for i, x in enumerate(user_ids)}
    user_encoded_to_user = {i: x for i, x in enumerate(user_ids)}
    
    anime_ids = df_train['anime_id'].unique().tolist()
    anime_to_anime_encoded = {x: i for i, x in enumerate(anime_ids)}
    anime_encoded_to_anime = {i: x for i, x in enumerate(anime_ids)}
    ```
    1. Encoding untuk kolom 'user_id':

        * User_ids diubah menjadi daftar unik menggunakan metode unique().
        * Kemudian, setiap nilai 'user_id' dienkripsi menjadi nilai yang lebih kecil menggunakan metode enumerate().
        * Dalam hal ini, user_to_user_encoded adalah kamus yang memetakan nilai asli 'user_id' ke nilai terenkripsi, sedangkan user_encoded_to_user adalah kamus yang memetakan nilai terenkripsi ke nilai asli 'user_id'.
    2. Encoding untuk kolom 'anime_id':

        * Anime_ids diubah menjadi daftar unik menggunakan metode unique().
        * Setiap nilai 'anime_id' dienkripsi menjadi nilai yang lebih kecil menggunakan metode enumerate().
        * anime_to_anime_encoded adalah kamus yang memetakan nilai asli 'anime_id' ke nilai terenkripsi, sedangkan anime_encoded_to_anime adalah kamus yang memetakan nilai terenkripsi ke nilai asli 'anime_id'.
        
        Dengan menggunakan metode encoding seperti ini, nilai unik dalam kolom 'user_id' dan 'anime_id' direpresentasikan dalam bentuk angka yang lebih kecil, sehingga memungkinkan penggunaan algoritma atau model yang membutuhkan input numerik.
        
2. Normalisasi nilai rating untuk memudahkan training hal ini bertujuan data untuk mengubahnya menjadi bentuk yang lebih terstandarisasi atau normal. Tujuan normalisasi adalah untuk menghilangkan perbedaan skala, mengurangi bias, atau menyesuaikan data agar dapat dibandingkan atau diproses dengan lebih baik.
3. Train-Test Split untuk melakukan validasi model dengan pembagian 80% data training dan 20% data testing

## Modeling

Dalam proyek ini, saya menggunakan dua jenis sistem rekomendasi yaitu *content-based filtering* (CBF) dan *collaborative filtering* (CF). Untuk CBF, saya akan menggunakan vektorisasi TF-IDF dan cosine similarity sebagai similarity function-nya.
Untuk kelebihan vektorisasi TF-IDF adalah :
1. Merepresentasikan kepentingan relatif kata dalam dokumen: Dengan menggunakan skema bobot TF-IDF, vektorisasi TF-IDF memberikan bobot yang lebih tinggi untuk kata-kata yang jarang muncul dalam dokumen tetapi muncul secara khusus dalam dokumen tertentu. Hal ini membantu dalam mengidentifikasi kata-kata kunci atau kata-kata yang paling mewakili dokumen.
2. Mengurangi dampak kata-kata umum: Vektorisasi TF-IDF secara inheren memberikan bobot yang lebih rendah untuk kata-kata umum yang muncul di banyak dokumen. Ini membantu dalam mengidentifikasi kata-kata yang lebih spesifik dan lebih deskriptif dari sebuah dokumen.
3. Efektif dalam mewakili dokumen panjang: Vektorisasi TF-IDF cenderung efektif dalam mengatasi masalah dokumen yang panjang dengan banyak kata. Bobot TF-IDF membantu dalam menyoroti kata-kata kunci yang unik dan penting dalam dokumen.

Untuk kekurangan vektorisasi TF-IDF :
1. Tidak memperhitungkan konteks kata: Vektorisasi TF-IDF hanya memperhitungkan keberadaan kata dalam dokumen dan frekuensi kemunculannya, tanpa memperhitungkan konteks kata. Artinya, informasi tentang urutan kata dan hubungannya tidak diperhitungkan dalam vektorisasi ini.
2. Tidak mempertimbangkan makna kata: Vektorisasi TF-IDF tidak mempertimbangkan makna kata-kata secara langsung. Hal ini dapat menyebabkan masalah jika kata-kata yang serupa secara makna tetapi berbeda secara ortografi diberikan bobot yang berbeda secara signifikan.

Kelebihan cosine similarity: 
1. Mengukur kesamaan semantik: Cosine similarity mengukur kesamaan antara dua vektor dokumen berdasarkan arah dan bukan panjang vektor. Ini memungkinkan pengukuran kesamaan yang lebih baik secara semantik daripada hanya menggunakan frekuensi kata.
2. Skala independen: Cosine similarity tidak tergantung pada skala data atau panjang dokumen. Hal ini memungkinkan perbandingan yang adil antara dokumen-dokumen dengan panjang yang berbeda.

Kekurangan cosine similarity:
1. Tidak memperhitungkan konteks kata: Seperti halnya vektorisasi TF-IDF, cosine similarity juga tidak memperhitungkan konteks kata. Informasi tentang urutan kata dan hubungannya tidak diperhitungkan dalam perhitungan kesamaan.
2. Rentan terhadap kata-kata umum: Cosine similarity tidak secara langsung mengurangi dampak kata-kata umum. Kata-kata yang sering muncul dalam banyak dokumen dapat memiliki bobot yang tinggi dan mempengaruhi hasil perhitungan kesamaan.

Untuk Pembentukan TF-IDF dapat menggunakan kodingan sebagai berikut:
```
tf = TfidfVectorizer()
tf.fit(anime_ovrl['genre']) 
tf.get_feature_names_out()
```
Kodingan tersebut memiliki arti sebagai berikut:

* tf = TfidfVectorizer(): Membuat objek dari kelas TfidfVectorizer, yang merupakan bagian dari modul sklearn.feature_extraction.text dalam library Scikit-learn. TfidfVectorizer digunakan untuk melakukan vektorisasi teks dengan metode Term Frequency-Inverse Document Frequency (TF-IDF).

* tf.fit(anime_ovrl['genre']): Menggunakan objek TfidfVectorizer (tf) untuk menghitung statistik TF-IDF dari data genre yang terdapat dalam kolom 'genre' dari dataframe anime_ovrl. Metode fit() digunakan untuk mengumpulkan statistik yang diperlukan untuk melakukan vektorisasi.

* tf.get_feature_names_out(): Mengembalikan daftar kata atau fitur yang dihasilkan dari vektorisasi teks menggunakan TF-IDF. Metode get_feature_names_out() digunakan untuk mendapatkan daftar fitur dari vektorisasi yang telah dilakukan.

Dengan menggunakan kodingan tersebut, dilakukan vektorisasi teks dengan metode TF-IDF pada data genre anime. Hasilnya adalah daftar fitur yang merepresentasikan kata-kata atau istilah yang muncul dalam genre anime, dengan bobot yang dihitung berdasarkan metode TF-IDF.

Hasil output dari CBF ada di Tabel 3 sebagai berikut:
Tabel 3. Hasil Pediksi menggunkana Model CBF

| No | Name | Genre |
|---------|------------|------------|
| 1   | Tenpo Ibun: Ayakashi Ayashi | Demons, Historikal, Supernatural |
| 2   | Kataku   | Demons, Historikal, Supernatural|
| 3     | Sengoku Choujuu Giga   | Demons, Historikal, Supernatural    |
| 4     | Kujakuo: Sengoku Tensei       | Action ,Demons, Historikal, Supernatural      |
| 5     | Chmo Crudase: Az Demo Wakaru Chrmo Crusade Kouza   | Comedy, Action ,Demons, Historikal, Supernatural    |

Dari Tabel 3 dapat dilihat kalau sistem ingin merekomendasikan judul "Oni" dengan genre demon, historikal, dan supernatural. Sistem dapat merekomendasikan dengan genre yang tepat dengan sesuai dan presisi.

Lalu untuk *collaborative filtering* (CF) merupakan salah satu metode yang digunakan dalam sistem rekomendasi untuk menyajikan rekomendasi kepada pengguna berdasarkan preferensi atau perilaku pengguna lain yang memiliki kesamaan dengan pengguna tersebut. Metode ini memanfaatkan informasi dari pengguna-pengguna lain atau item-item yang serupa untuk memberikan rekomendasi.

Kelebihan CF:
1. Memperhitungkan preferensi pengguna: Collaborative filtering memperhitungkan preferensi pengguna berdasarkan data riwayat pengguna atau perilaku pengguna lain yang memiliki kesamaan dengan pengguna target. Hal ini memungkinkan rekomendasi yang lebih personal dan relevan dengan preferensi pengguna.
2. Tidak membutuhkan informasi konten: Collaborative filtering tidak membutuhkan informasi rinci tentang item atau konten yang direkomendasikan. Ini memungkinkan sistem rekomendasi untuk memberikan rekomendasi bahkan jika tidak ada informasi konten yang tersedia.
3. Dapat menemukan preferensi baru: Collaborative filtering dapat menemukan preferensi baru yang mungkin tidak terdeteksi oleh metode rekomendasi lainnya. Hal ini terjadi ketika pengguna memiliki preferensi yang sama dengan pengguna lain yang tidak terduga.

Kekurangan CF:
1. Masalah cold start: Collaborative filtering menghadapi masalah cold start ketika sistem tidak memiliki informasi yang cukup tentang pengguna baru atau item baru. Dalam situasi ini, sulit untuk memberikan rekomendasi yang akurat karena tidak ada data riwayat yang cukup untuk digunakan dalam perhitungan rekomendasi.
2. Masalah skalabilitas: Ketika jumlah pengguna dan item sangat besar, perhitungan kesamaan dan penyimpanan data kolaboratif bisa menjadi rumit dan memakan waktu. Hal ini dapat mempengaruhi kinerja sistem rekomendasi dan memerlukan infrastruktur yang kuat untuk menangani volume data yang besar.
3. Efek "filter bubble": Collaborative filtering cenderung memperkuat preferensi yang ada dan membentuk apa yang disebut "filter bubble". Pengguna mungkin terpapar dengan rekomendasi yang serupa dan tidak cukup beragam, sehingga mengurangi variasi dan eksplorasi pengguna dalam menemukan hal-hal baru.

Penggunaan collaborative filtering yang efektif membutuhkan jumlah data yang signifikan dan keberadaan pengguna dan item yang serupa. Selain itu, perlu memperhatikan dan mengatasi masalah cold start dan efek "filter bubble" untuk memberikan rekomendasi yang berkualitas.

Rekomendasi yang diinputkan oleh user 2342 pada Tabel 4.
Tabel 4. Rekomendasi yang diberikan oleh user
| NO |Judul  | Genre |
|---------|---------|------------|
|1 | Onegai☆Teacher | Comedy, Drama, Romance, School, Sci-Fi|
| 2| Kidou Senkan Nadesico  | The Prince of Darkness : Action, Comedy, Drama, Mecha, Psychological, Sci-Fi, Shounen, Space|
| 3| Makai Toshi Shinjuku   | Adventure, Horror, Romance, Shounen, Supernatural   |

Lalu hasil Rekomendasi yang diprediksi oleh sistem dapat dilihat pada Tabel 5.
Tabel 5. Hasil Prediksi Rekomendasi Sistem
| NO |Judul  | Genre |
|---------|---------|------------|
|1 | Onegai☆Teacher: Himitsu na Futari | Comedy, Ecchi, Romance, Sci-Fi|
| 2| Kataku   | Demons, Historikal, Supernatural|
| 3| Nils no Fushigi na Tabi   | Adventure, Fantasy, Kids    |
| 4| Nozomi Witches   | Romance, Sports    |
| 5| Grey   | Digital Target : Action, Fantasy, Sci-Fi   |
| 6| Choujin Densetsu Urotsukidouji: Mirai-hen  | Demons, Fantasy, Hentai, Horror, Sci-Fi    |
| 7| Yukiyo Ichiya Monogatari   | Hentai, Historical    |

## Evaluation
Dalam proyek ini penulis menggunakan metrik MAE(Mean Absolute Error) untuk *collaborative filtering* dan perhitungan manual presisi untuk *content-based filtering*. MAE merupakan metrik evaluasi yang digunakan untuk mengukur kesalahan atau selisih antara nilai prediksi dan nilai aktual dalam konteks pemodelan atau peramalan. MAE mengukur kesalahan rata-rata secara absolut, yaitu selisih antara nilai prediksi dan nilai aktual tanpa mempertimbangkan arah atau signifikansi dari selisih tersebut. MAE menghitung nilai absolut dari setiap selisih dan kemudian mengambil rata-rata dari seluruh nilai absolut tersebut. MAE memiliki skala yang sama dengan variabel yang diukur, sehingga lebih mudah untuk diinterpretasikan daripada metrik evaluasi lainnya seperti Mean Squared Error (MSE) yang memiliki skala kuadrat.

![MAE](https://i.ibb.co/xzLxD31/mae.png)
Gambar 2. Rumus MAE
Rincian Sistematis rumus MAE pada Gambar 2 dapat dilihat sebagai berikut:

* MAE adalah Mean Absolute Error.
* n adalah jumlah sampel atau observasi.
* Σ adalah simbol sigma yang menunjukkan penjumlahan.
* yi adalah nilai aktual atau nilai yang diamati.
* xi adalah nilai prediksi atau nilai yang diprediksi.

Semakin rendah nilai MAE, semakin baik kualitas prediksi atau model yang digunakan. MAE digunakan dalam berbagai bidang seperti statistik, pemodelan data, dan machine learning untuk mengevaluasi kinerja model dalam memprediksi nilai atau variabel tertentu.

Lalu untuk model yang dihasilkan MAE terukur naik secara signifikan, hal ini dapat dilihat pada Gambar 3:

![Hasil MAE](https://i.ibb.co/bgGLrw6/hasil-MAE.png)
Gambar 3. Hasil MAE Menggunakan *collaborative filtering*

Pada Gambar 3 dapat dilihat kalau model *collaborative filtering* tidak cocok dengan data yang diujikan, hal ini dapat dipengaruhi beberapa faktor seperti:

1. Sparsitas data: Jika data kolaboratif memiliki banyak kekosongan atau kekurangan interaksi antara pengguna dan item, ini dapat menyebabkan nilai MAE yang tinggi. Ketika terdapat sedikit informasi atau interaksi yang tersedia untuk memperkirakan preferensi pengguna, prediksi yang dihasilkan cenderung kurang akurat.
2. Heterogenitas preferensi pengguna: Jika preferensi pengguna sangat beragam atau heterogen, ini dapat meningkatkan nilai MAE. Dalam situasi ini, sulit untuk menemukan pengguna yang memiliki preferensi yang mirip atau tetangga yang relevan untuk membuat prediksi yang akurat.
3. Data yang tidak lengkap atau tidak akurat: Jika data kolaboratif mengandung nilai yang hilang, data yang tidak lengkap, atau kesalahan dalam nilai, hal ini dapat mengganggu kemampuan model collaborative filtering untuk memberikan prediksi yang akurat. Data yang buruk atau tidak lengkap dapat menghasilkan kesalahan dalam perhitungan kesamaan atau estimasi preferensi.
4. Kurangnya informasi kontekstual: Collaborative filtering cenderung hanya mempertimbangkan interaksi antara pengguna dan item tanpa mempertimbangkan faktor kontekstual yang mungkin mempengaruhi preferensi pengguna. Faktor-faktor seperti waktu, lokasi, atau situasi yang dapat memengaruhi preferensi tidak dipertimbangkan secara eksplisit dalam metode collaborative filtering tradisional.
5. Kurangnya diversitas rekomendasi: Jika sistem collaborative filtering cenderung memberikan rekomendasi yang terlalu serupa atau kurang beragam, hal ini dapat menyebabkan nilai MAE yang tinggi. Pengguna mungkin memperoleh rekomendasi yang tidak cukup bervariasi atau tidak mampu menemukan preferensi baru yang berbeda dari preferensi yang sudah ada.
6. Masalah cold start: Masalah cold start muncul ketika sistem tidak memiliki informasi yang cukup tentang pengguna baru atau item baru. Dalam situasi ini, sulit untuk memberikan rekomendasi yang akurat karena kurangnya data riwayat atau interaksi.

Mengatasi faktor-faktor ini dapat membantu dalam mengurangi nilai MAE yang tinggi pada collaborative filtering. Beberapa pendekatan termasuk penggunaan teknik pengisian nilai yang hilang, peningkatan metode penghitungan kesamaan, penggunaan metode ensemble, dan memperkaya data dengan informasi kontekstual.

Lalu untuk *content-based filtering*, perhitungan presisi menggunakan perhitungan manual seperti rumus dibawah ini. 

$$Precision = \frac{{\text{{\# of recommendation that are relevant}}}}{{\text{{\# of items we recommend}}}}$$

Dalam rumus di atas dapat dilihat rumus preisi untuk rekomendasi sistem berbasis *content-based filtering* menggunakan perhitungan manual dengan cara membagi nilai rekomendasi yang relevan dengan item rekomendasi yang direkomendasikan. 

Tabel 6. Mengetahui hasil metrik yang dihasilkan
| No | Name | Genre |
|---------|------------|------------|
| 1   | Tenpo Ibun: Ayakashi Ayashi | Demons, Historikal, Supernatural |
| 2   | Kataku   | Demons, Historikal, Supernatural|
| 3     | Sengoku Choujuu Giga   | Demons, Historikal, Supernatural    |
| 4     | Kujakuo: Sengoku Tensei       | Action ,Demons, Historikal, Supernatural      |
| 5     | Chmo Crudase: Az Demo Wakaru Chrmo Crusade Kouza   | Comedy, Action ,Demons, Historikal, Supernatural    |

untuk anime "Oni" sendiri memiliki Genre Demons, Historical, Supernatural dengan jumlah variabel lebih dari satu. Dari Tabel 6 dapat dilihat kalau ada 5 item yang memiliki genre yang sama dengan anime "Oni". Artinya presisi sistem yang dihasilkan sebesar 5/5 atau 100%.

Hal ini sesuai rumus yang ditunjukkan pada rumus sebelumnya.
Precision = #of recommendation that are relevant/#of item we recommend.
Pada Hasil rekomendasi pada Tabel 6:
Precission = 5/5.
Jadi presisinya = 100%





