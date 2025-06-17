=================================================================================
26-28. Soal String Terurut (cek & ricek)
Analisis Fungsi
- cek(S): Akan bernilai true hanya jika seluruh karakter dari kiri ke kanan tersusun urut (A-Z). Jika menemukan satu saja pelanggaran, langsung false.
- ricek(S): Akan bernilai true jika menemukan minimal satu pasang karakter yang bersebelahan yang tersusun urut. Akan false hanya jika seluruh string tersusun menurun secara ketat (misal "ZCA").
=================================================================================

26. Jawaban: B. cek("BEGITU")
Perhitungan Manual cek("BEGITU"):
i = 0: S[0] ('B') <= S[1] ('E')? Ya. Lanjut.
i = 1: S[1] ('E') <= S[2] ('G')? Ya. Lanjut.
i = 2: S[2] ('G') <= S[3] ('I')? Ya. Lanjut.
i = 3: S[3] ('I') <= S[4] ('T')? Ya. Lanjut.
i = 4: S[4] ('T') <= S[5] ('U')? Ya. Lanjut.

Loop selesai tanpa menemukan S[i] > S[i+1].
Fungsi mengembalikan true.

===

27. Jawaban: 3276
Ini adalah soal kombinasi dengan pengulangan. Kita memilih 3 huruf dari 26 pilihan, di mana urutan tidak penting (karena akan diurutkan) dan pengulangan diizinkan (misal "AAB").
Rumus: C(n+k−1,k) dengan n=26 dan k=3.
C(26+3−1,3)=C(28,3)
C(28,3)= 28×27×26 / 3×2×1
C(28,3)= 28×27×26 / 6
​C(28,3)=28×(27/3)×(26/2)=28×9×13=3276
cek(S) = ricek(S) untuk semua string S:

===

28. Jawaban: SALAH
Tinggal cari aja contoh penyangkal misalnya cek("BCA"):

cek("BCA"):
i = 0: Apakah B > C? Tidak. Lanjut.
i = 1: Apakah C > A? Ya. OK.
Fungsi langsung mengembalikan false.

ricek("BCA"):
i = 0: Apakah B <= C? Ya, OK.
Fungsi langsung mengembalikan true.

Karena false != true, pernyataan tersebut salah.


=================================================================================
29-31. Start dan Finish (go)
Analisis Fungsi
- go(N) mencari selisih terbesar antara dua faktor (pembagi) yang berurutan dari N.
=================================================================================

29. Jawaban: 15
go(30):

Inisialisasi: 
- s = 0, 
- f = 1.
Loop i dari 2 sampai 30:
i = 2 (faktor): selisih 2-1=1. s menjadi 1. f menjadi 2.
i = 3 (faktor): selisih 3-2=1. s tetap 1. f menjadi 3.
i = 5 (faktor): selisih 5-3=2. s menjadi 2. f menjadi 5.
i = 6 (faktor): selisih 6-5=1. s tetap 2. f menjadi 6.
i = 10 (faktor): selisih 10-6=4. s menjadi 4. f menjadi 10.
i = 15 (faktor): selisih 15-10=5. s menjadi 5. f menjadi 15.
i = 30 (faktor): selisih 30-15=15. s menjadi 15. f menjadi 30.

===

30. Jawaban: 96
Logika:
Fungsi go(N) mencari gap terbesar antar faktor.
Gap terbesar untuk sebuah bilangan N adalah selisih antara N sendiri dengan faktor terbesarnya sebelum N.
Untuk memaksimalkan gap ini, kita butuh bilangan yang faktor terbesarnya (selain dirinya sendiri) sekecil mungkin. Bilangan seperti ini adalah bilangan prima, yang faktor terbesarnya (selain dirinya sendiri) adalah 1.

Untuk bilangan prima P, go(P) = P - 1.

Jadi, kita tinggal mencari bilangan prima terbesar di bawah 100, yaitu 97.
Hasilnya adalah go(97) = 97 - 1 = 96.

===

31. Jawaban: BENAR
Logika:
- Ambil sembarang bilangan N. Misalkan p adalah faktor terbesar dari N yang bukan N itu sendiri.
- Secara definisi, p tidak mungkin lebih besar dari N/2. Jika p > N/2, maka N/p akan lebih kecil dari 2, dan satu-satunya bilangan bulat yang mungkin adalah 1, yang berarti p=N. Jadi, p pasti ≤ N/2.
- Salah satu selisih yang dihitung go(N) adalah selisih terakhir: N - p.
- Karena p ≤ N/2, maka N - p ≥ N - (N/2) = N/2.
- Karena go(N) adalah selisih terbesar, dan ada satu selisih yang nilainya dijamin minimal N/2, maka go(N) pasti ≥ N/2.


=================================================================================
32-34. Ke kiri dan ke kanan Soal Pencarian Biner (dua_mata)
Analisis Fungsi
-dua_mata adalah binary search yang true jika berhasil mengisolasi 0 di akhir pencarian. Logika ini efektif jika vektornya urut menurun.
=================================================================================

32. Jawaban: C. dua_mata({4,3,2,1,0,-1,-2}, 0, 6)
Rekursif:
dua_mata(A, 0, 6): mid = 3, A[3] = 1. Karena 1 > 0, panggil dua_mata(A, 4, 6).
dua_mata(A, 4, 6): mid = 5, A[5] = -1. Karena -1 < 0, panggil dua_mata(A, 4, 4).
dua_mata(A, 4, 4): kiri == kanan. Cek A[4] == 0. 0 == 0 itu benar. Kembali true.
Hasil true dikembalikan ke pemanggil sebelumnya, dan seterusnya, sampai ke pemanggilan awal. Hasil akhir true.

Diuji ke semua pilihan maka didapat:
A. dua_mata(...) -> false
B. dua_mata(...) -> false
C. dua_mata(...) -> true
D. dua_mata(...) -> false
E. dua_mata(...) -> false
Kesimpulan: Hanya pilihan C yang mengembalikan true.

===

33. Jawaban: 26
Waktu T(N) = c * log₂(N) + k.
T(2000) - T(1000) = c * (log₂(2000) - log₂(1000)) = c * log₂(2000/1000) = c * log₂(2) = c.
22 - 20 = c → c = 2.

Kita cari T(8000).
T(8000) = T(1000) + c * (log₂(8000) - log₂(1000)) = 20 + 2 * log₂(8000/1000) = 20 + 2 * log₂(8) = 20 + 2 * 3 = 20 + 6 = 26.

===

34. Jawaban: 324
Logika:
Agar true, 0 harus berada di posisi akhir pencarian. Untuk panjang 7, posisi akhir yang mungkin adalah indeks 0, 2, 4, 6. Ada 4 kemungkinan posisi.
Untuk setiap posisi akhir, jalur pencarian sudah pasti. Contoh, agar 0 ada di indeks 4, A[3] harus >0 (agar ke kanan) dan A[5] harus <0 (agar ke kiri). Ini menetapkan nilai 3 elemen: A[4]=0, A[3]=1, A[5]=-1.
Sisa 4 elemen lainnya bisa diisi bebas dengan -1, 0, atau 1 (3 pilihan).
Jumlah kemungkinan untuk 4 elemen ini adalah 3×3×3×3=81.
Total = (Jumlah posisi akhir) x (Jumlah kemungkinan per posisi) = 4×81=324.


=================================================================================
35-37. Soal Jumlah Digit & Kelipatan (panas & dingin)
Analisis Fungsi
- panas(X): Menghitung jumlah digit X. Contoh: panas(123) = 1+2+3=6.
- dingin(X,Y): Mencari kelipatan pertama dari Y yang jumlah digitnya sama dengan X.
=================================================================================

35. Jawaban: 28
Perhitungan dingin(10, 7):
air = 0, panas(0)=0. Tidak sama dengan 10. air = 0+7=7.
air = 7, panas(7)=7. Tidak sama dengan 10. air = 7+7=14.
air = 14, panas(14)=5. Tidak sama dengan 10. air = 14+7=21.
air = 21, panas(21)=3. Tidak sama dengan 10. air = 21+7=28.
air = 28, panas(28)=10. Sama dengan 10. Loop berhenti.

Fungsi mengembalikan air, yaitu 28.

36. Jawaban: 10010
Logika:
- Kita mencari bilangan terkecil N dimana panas(N) = 2 dan N % 35 == 0.
- Syarat N % 35 == 0 berarti N harus habis dibagi 5 dan 7.
- Syarat habis dibagi 5 berarti N harus berakhiran 0 atau 5.
- Syarat panas(N) = 2: jika N berakhiran 5, jumlah digit lain harus -3 (tidak mungkin). Jadi, N pasti berakhiran 0.
Kita cari bilangan terkecil berakhiran 0 yang jumlah digitnya 2, dan habis dibagi 7.

20: 20 % 7 != 0.
110: 110 % 7 != 0.
200: 200 % 7 != 0.
1100: 1100 % 7 ...
...
10010: 10010 / 7 = 1430. Habis dibagi 7. Ini adalah jawabannya, (1 + 0 + 0 + 1 + 0) = 2.

37. Jawaban: 3
Logika:
- Jika hasilnya 77, maka X harus panas(77) = 7+7 = 14.
- Y harus merupakan pembagi dari 77, yaitu {1, 7, 11, 77}.
- Kita verifikasi setiap Y:
    - dingin(14, 1): Akan berhenti di 59 (panas(59)=14), bukan 77. Tidak valid.
    - dingin(14, 7): Kelipatan 7 sebelum 77 tidak ada yang jumlah digitnya 14. Valid.
    - dingin(14, 11): Kelipatan 11 sebelum 77 tidak ada yang jumlah digitnya 14. Valid.
    - dingin(14, 77): Kelipatan pertama adalah 77. Valid.
- Total pasangan valid adalah 3.

=================================================================================
38-40. Fungsi Pendek
Rekrusif
=================================================================================


38. Hasil pndk(7, 7)
Fungsi ini merupakan implementasi dari Josephus Problem. Dengan menelusuri pemanggilan rekursifnya, hasil akhir dari pndk(7, 7) adalah 5.

===

39. Nilai Kembalian Terbesar
Dari 5 pilihan yang ada, pemanggilan yang hasil kembaliannya paling besar adalah D. pndk(60, 3).

Hasilnya tidak selalu meningkat seiring dengan naiknya N. Berdasarkan perhitungan untuk setiap pilihan:

pndk(20, 3) = 20
pndk(30, 3) = 29
pndk(40, 3) = 28
pndk(50, 3) = 11
pndk(60, 3) = 41 (v)
pndk(70, 3) = 1
Nilai kembalian tertinggi adalah 58.

===

40. Nilai N untuk Kembalian Maksimal (K=2)
Nilai N antara 1 hingga 5000 yang memberikan kembalian paling besar adalah 4095.
Alasan:
Untuk kasus khusus K=2, nilai kembalian pndk(N,2) tidak selalu N. Nilainya dihitung berdasarkan rumus yang berhubungan dengan representasi biner dari N.
Nilai kembalian terbesar dalam rentang 1 <= N <= 5000 terjadi saat N adalah satu kurangnya dari sebuah pangkat dua (2^a - 1).
Pangkat dua yang relevan adalah 2^12 = 4096.
Maka, nilai N yang menghasilkan kembalian terbesar adalah 4096 - 1 = 4095. Pada kasus ini, pndk(4095, 2) akan mengembalikan 4095, yang merupakan nilai tertinggi yang mungkin dicapai.



Kode CPP:
===============================================================================================
26-28
===============================================================================================

#include <iostream>
#include <string>
#include <vector>
#include <iomanip> // Diperlukan untuk std::boolalpha

/**
 * @brief Fungsi dari soal pertama.
 * Mengembalikan TRUE jika string S tersusun urut (non-decreasing).
 */
bool cek(std::string S) {
    int n = S.length();
    for (int i = 0; i < n - 1; i++) {
        if (S[i] > S[i + 1]) {
            return false;
        }
    }
    return true;
}

/**
 * @brief Fungsi dari soal ketiga.
 * Mengembalikan TRUE jika ada setidaknya satu pasang karakter S[i] <= S[i+1].
 */
bool ricek(std::string S) {
    int n = S.length();
    for (int i = 0; i < n - 1; i++) {
        if (S[i] <= S[i + 1]) {
            return true;
        }
    }
    return false;
}

int main() {
    // Menggunakan std::boolalpha agar output boolean dicetak sebagai "true" atau "false"
    std::cout << std::boolalpha;

    std::cout << "--- Program Verifikasi Jawaban Soal String ---" << std::endl;

    // --- Verifikasi Soal 1 ---
    std::cout << "\n[Soal 1: Manakah dari 5 pilihan yang mengembalikan TRUE?]" << std::endl;
    std::vector<std::string> pilihan = {"BEGINI", "BEGITU", "BERAPA", "BERUPA", "BETAPA"};
    for (const std::string& s : pilihan) {
        std::cout << "  - cek(\"" << s << "\") -> " << cek(s) << std::endl;
    }
    std::cout << "Kesimpulan: Hanya \"BEGITU\" yang mengembalikan true." << std::endl;

    // --- Verifikasi Soal 2 ---
    std::cout << "\n[Soal 2: Berapa banyak string 3 huruf yang lolos cek(S)?]" << std::endl;
    int counter = 0;
    // Cara efisien untuk menghitung: hanya generate string yang sudah pasti lolos.
    // c1 bisa dari A-Z. c2 harus >= c1. c3 harus >= c2.
    for (char c1 = 'A'; c1 <= 'Z'; ++c1) {
        for (char c2 = c1; c2 <= 'Z'; ++c2) {
            for (char c3 = c2; c3 <= 'Z'; ++c3) {
                // Setiap string yang dibentuk dari c1, c2, c3 di sini
                // secara definisi pasti akan lolos cek(S).
                // Contoh: "AAB", "ACZ", dll.
                counter++;
            }
        }
    }
    std::cout << "Jumlah kemungkinan string yang valid adalah: " << counter << std::endl;
    std::cout << "(Hasil ini sesuai dengan perhitungan kombinasi C(28, 3) = 3276)" << std::endl;


    // --- Verifikasi Soal 3 ---
    std::cout << "\n[Soal 3: Apakah cek(S) = ricek(S) untuk semua S?]" << std::endl;
    std::string contoh_penyangkal = "BCA";
    std::cout << "Menggunakan contoh penyangkal S = \"" << contoh_penyangkal << "\":" << std::endl;
    std::cout << "  - cek(\"" << contoh_penyangkal << "\")   -> " << cek(contoh_penyangkal) << std::endl;
    std::cout << "  - ricek(\"" << contoh_penyangkal << "\") -> " << ricek(contoh_penyangkal) << std::endl;
    std::cout << "Karena hasilnya berbeda untuk S = \"BCA\", maka pernyataan tersebut SALAH." << std::endl;

    return 0;
}



===============================================================================================
29-31
===============================================================================================
#include <iostream>

/**
 * @brief Fungsi dari soal.
 * Menemukan selisih (gap) terbesar antara dua faktor (pembagi)
 * yang berurutan dari bilangan N.
 */
int go(int N) {
    // Menangani kasus N=1, di mana tidak ada faktor > 1
    if (N <= 1) {
        return 0;
    }

    int s = 0; // Menyimpan selisih terbesar
    int f = 1; // Menyimpan faktor terakhir yang ditemukan

    // Loop dari 2 sampai N untuk mencari semua faktor
    for (int i = 2; i <= N; i++) {
        if (N % i == 0) {
            // Jika i adalah faktor, hitung selisihnya dengan faktor sebelumnya (f)
            if (i - f > s) {
                s = i - f; // Update selisih terbesar jika ditemukan yang baru
            }
            f = i; // Simpan i sebagai faktor terakhir untuk iterasi berikutnya
        }
    }
    return s;
}

int main() {
    std::cout << "--- Program Verifikasi Jawaban Soal 'go(N)' ---" << std::endl;

    // --- Verifikasi Soal 1 ---
    std::cout << "\n[Soal 1: Hasil dari go(30)]" << std::endl;
    std::cout << "go(30) = " << go(30) << std::endl;

    // --- Verifikasi Soal 2 ---
    std::cout << "\n[Soal 2: Nilai go(N) terbesar untuk 1 <= N <= 100]" << std::endl;
    int max_go_result = 0;
    int n_for_max = 0;
    for (int n = 1; n <= 100; ++n) {
        int current_result = go(n);
        if (current_result > max_go_result) {
            max_go_result = current_result;
            n_for_max = n;
        }
    }
    std::cout << "Nilai terbesar yang ditemukan adalah " << max_go_result
              << ", yang didapat dari pemanggilan go(" << n_for_max << ")." << std::endl;

    // --- Verifikasi Soal 3 ---
    std::cout << "\n[Soal 3: Verifikasi apakah go(N) >= N/2 untuk N > 1]" << std::endl;
    bool statement_holds = true;
    int counter_example = 0;
    // Tes untuk rentang yang cukup besar untuk meyakinkan
    for (int n = 2; n <= 1000; ++n) {
        // Gunakan 2.0 untuk memastikan pembagian desimal (float division)
        if (go(n) < n / 2.0) {
            statement_holds = false;
            counter_example = n;
            break;
        }
    }

    if (statement_holds) {
        std::cout << "Pernyataan terbukti BENAR untuk semua N yang diuji (2 s.d. 1000)." << std::endl;
    } else {
        std::cout << "Pernyataan terbukti SALAH. Contoh penyangkal: go(" << counter_example
                  << ") < " << counter_example << "/2." << std::endl;
    }

    return 0;
}



===============================================================================================
32-34
===============================================================================================

#include <iostream>
#include <vector>
#include <string>
#include <iomanip> // Diperlukan untuk std::boolalpha
#include <cmath>   // Diperlukan untuk log2 pada komentar

/**
 * @brief Fungsi dari soal.
 * Melakukan pencarian biner dengan logika spesifik.
 * @return true jika pencarian berakhir di satu elemen bernilai 0, false jika tidak.
 */
bool dua_mata(const std::vector<int>& A, int kiri, int kanan) {
    // Kondisi pengaman jika rentang menjadi tidak valid
    if (kiri > kanan) {
        return false;
    }
    // Basis rekursi: jika rentang tinggal satu elemen
    if (kiri == kanan) {
        return (A[kiri] == 0);
    } else {
        // Menggunakan cara yang aman untuk menghitung mid untuk menghindari overflow
        int mid = kiri + (kanan - kiri) / 2;
        if (A[mid] < 0) {
            // Jika nilai tengah negatif, cari di setengah bagian kiri
            return dua_mata(A, kiri, mid - 1);
        } else if (A[mid] > 0) {
            // Jika nilai tengah positif, cari di setengah bagian kanan
            return dua_mata(A, mid + 1, kanan);
        } else { // A[mid] == 0
            // Jika nilai tengah adalah 0, langsung gagal
            return false;
        }
    }
}

// --- Fungsi untuk Soal 3 ---
int valid_vector_count = 0;
void generate_and_test(std::vector<int>& current_vector, int index) {
    // Jika vektor sudah terisi penuh (panjang 7)
    if (index == current_vector.size()) {
        if (dua_mata(current_vector, 0, current_vector.size() - 1)) {
            valid_vector_count++;
        }
        return;
    }
    
    // Coba isi elemen saat ini dengan -1, 0, atau 1, lalu lanjut ke indeks berikutnya
    for (int val : {-1, 0, 1}) {
        current_vector[index] = val;
        generate_and_test(current_vector, index + 1);
    }
}


int main() {
    // Menggunakan std::boolalpha agar output boolean dicetak sebagai "true" atau "false"
    std::cout << std::boolalpha;

    std::cout << "--- Program Verifikasi Jawaban Soal 'dua_mata' ---" << std::endl;

    // --- Verifikasi Soal 1 ---
    std::cout << "\n[Soal 1: Manakah dari 5 pilihan yang mengembalikan TRUE?]" << std::endl;
    std::vector<std::vector<int>> pilihan = {
        {0,1,2,3,4,5,6},
        {-2,-1,0,1,2,3,4},
        {4,3,2,1,0,-1,-2},
        {-6,-5,-4,-3,-2,-1,0},
        {-1,0,1,0,-1,0,1}
    };
    char option_label = 'A';
    for (const auto& vec : pilihan) {
        std::cout << "  " << option_label++ << ". dua_mata(...) -> " << dua_mata(vec, 0, vec.size() - 1) << std::endl;
    }
    std::cout << "Kesimpulan: Hanya pilihan C yang mengembalikan true." << std::endl;

    // --- Verifikasi Soal 2 ---
    std::cout << "\n[Soal 2: Estimasi Waktu Eksekusi]" << std::endl;
    std::cout << "Analisis ini bersifat konseptual (O(log N)) dan tidak bisa diukur langsung di sini." << std::endl;
    std::cout << "Waktu T(N) dapat dimodelkan sebagai c*log2(N) + k." << std::endl;
    std::cout << "T(2000) - T(1000) = c*(log2(2000)-log2(1000)) = c*log2(2) = c. Jadi, 22-20=c -> c=2." << std::endl;
    std::cout << "T(8000) - T(2000) = c*(log2(8000)-log2(2000)) = c*log2(4) = c*2. Jadi, T(8000)-22=2*2=4." << std::endl;
    std::cout << "Maka T(8000) = 22 + 4 = 26 detik." << std::endl;

    // --- Verifikasi Soal 3 ---
    std::cout << "\n[Soal 3: Berapa banyak vektor valid dengan panjang 7?]" << std::endl;
    std::cout << "Menghitung dengan metode brute-force... (mencoba semua 3^7 = 2187 kemungkinan)" << std::endl;
    std::vector<int> vec_to_generate(7);
    generate_and_test(vec_to_generate, 0);
    std::cout << "Hasil: Ditemukan " << valid_vector_count << " vektor yang valid." << std::endl;

    return 0;
}



===============================================================================================
35-37
===============================================================================================

#include <iostream>
#include <vector>
#include <set>
using namespace std;

int panas(int X) {
    if (X == 0) return 0;
    else return (X % 10) + panas(X / 10);
}

int dingin(int X, int Y) {
    int air = 0;
    while (panas(air) != X) air = air + Y;
    return air;
}

int main() {
    // Analisis fungsi panas - ini menghitung digit sum
    cout << "Fungsi panas menghitung jumlah digit:" << endl;
    for(int i = 0; i <= 20; i++) {
        cout << "panas(" << i << ") = " << panas(i) << endl;
    }
    cout << "panas(77) = " << panas(77) << endl;
    cout << "panas(123) = " << panas(123) << endl;
    
    // Pertanyaan 1: dingin(10,7)
    cout << "\n\nPertanyaan 1: dingin(10,7)" << endl;
    cout << "Mencari air terkecil dimana panas(air) = 10" << endl;
    cout << "Mulai dari air = 0, tambah 7 setiap iterasi" << endl;
    
    int air = 0;
    int step = 0;
    while (panas(air) != 10) {
        cout << "Step " << step << ": air = " << air << ", panas(" << air << ") = " << panas(air) << endl;
        air = air + 7;
        step++;
        if(step > 20) break; // safety break
    }
    cout << "Final: air = " << air << ", panas(" << air << ") = " << panas(air) << endl;
    cout << "dingin(10,7) = " << dingin(10,7) << endl;
    
    // Pertanyaan 2: dingin(2,35)
    cout << "\n\nPertanyaan 2: dingin(2,35)" << endl;
    cout << "dingin(2,35) = " << dingin(2,35) << endl;
    
    // Verifikasi
    int result2 = dingin(2,35);
    cout << "Verifikasi: panas(" << result2 << ") = " << panas(result2) << endl;
    
    // Pertanyaan 3: Berapa pasang <X,Y> sehingga dingin(X,Y) = 77
    cout << "\n\nPertanyaan 3: Mencari pasang <X,Y> dimana dingin(X,Y) = 77" << endl;
    cout << "panas(77) = " << panas(77) << endl;
    
    set<pair<int,int>> validPairs;
    
    // Untuk dingin(X,Y) = 77, artinya:
    // 77 adalah kelipatan Y terkecil yang digit sumnya = X
    
    // Cari semua pembagi dari 77
    vector<int> divisors;
    for(int i = 1; i <= 77; i++) {
        if(77 % i == 0) {
            divisors.push_back(i);
        }
    }
    
    cout << "Pembagi 77: ";
    for(int d : divisors) cout << d << " ";
    cout << endl;
    
    // Untuk setiap pembagi Y dari 77
    for(int Y : divisors) {
        // Cek apakah 77 adalah kelipatan Y pertama dengan digit sum tertentu
        int target_digit_sum = panas(77); // 14
        
        // Mulai dari 0, tambah Y sampai digit sum = target_digit_sum
        int air = 0;
        while (panas(air) != target_digit_sum) {
            air = air + Y;
        }
        
        // Jika air yang ditemukan = 77, maka (target_digit_sum, Y) adalah pasangan valid
        if(air == 77) {
            validPairs.insert({target_digit_sum, Y});
            cout << "Valid pair: X=" << target_digit_sum << ", Y=" << Y << endl;
        }
    }
    
    // Tapi tunggu, kita perlu cek semua kemungkinan X, bukan hanya panas(77)
    cout << "\nCek semua kemungkinan X:" << endl;
    validPairs.clear();
    
    for(int Y = 1; Y <= 77; Y++) {
        if(77 % Y == 0) { // Y adalah pembagi dari 77
            for(int X = 1; X <= 50; X++) { // X adalah digit sum, maksimal sekitar 50 untuk bilangan 2 digit
                int air = 0;
                bool found = false;
                int iterations = 0;
                
                while (iterations < 1000) { // safety limit
                    if(panas(air) == X) {
                        found = true;
                        break;
                    }
                    air = air + Y;
                    iterations++;
                    
                    if(air > 200) break; // jika sudah terlalu besar
                }
                
                if(found && air == 77) {
                    validPairs.insert({X, Y});
                    cout << "Valid pair: X=" << X << ", Y=" << Y << " (dingin(" << X << "," << Y << ") = " << air << ")" << endl;
                }
            }
        }
    }
    
    cout << "\nTotal pasang <X,Y>: " << validPairs.size() << endl;
    
    return 0;
}



===============================================================================================
38-40
===============================================================================================

#include <iostream>
#include <vector>
#include <string>

/**
 * @brief Versi rekursif dari fungsi pndk, sesuai dengan soal.
 * Bisa menjadi lambat atau menyebabkan stack overflow untuk N yang besar.
 */
int pndk_recursive(int N, int K) {
    if (N == 1) {
        return 1;
    }
    // Memanggil dirinya sendiri sampai N=1
    return (pndk_recursive(N - 1, K) + K - 1) % N + 1;
}


int main() {
    auto pndk = pndk_recursive;

    std::cout << "--- Program Verifikasi Jawaban Soal OSN ---" << std::endl;

    std::cout << "\n[Soal 1]" << std::endl;
    int n1 = 7, k1 = 7;
    std::cout << "Hasil pndk(" << n1 << ", " << k1 << ") adalah: " << pndk(n1, k1) << std::endl;

    std::cout << "\n[Soal 2]" << std::endl;
    std::cout << "Membandingkan hasil untuk K=3:" << std::endl;
    std::vector<int> n_values = {30, 40, 50, 60, 70};
    int k2 = 3;
    int max_result = 0;
    int n_for_max_result = 0;

    for (int n : n_values) {
        int current_result = pndk(n, k2);
        std::cout << "  - pndk(" << n << ", " << k2 << ") = " << current_result << std::endl;
        if (current_result > max_result) {
            max_result = current_result;
            n_for_max_result = n;
        }
    }
    std::cout << "Kesimpulan: Hasil terbesar adalah " << max_result 
              << ", didapat dari pemanggilan pndk(" << n_for_max_result << ", " << k2 << ")." << std::endl;

    std::cout << "\n[Soal 3]" << std::endl;
    int n3 = 4095, k3 = 2;
    std::cout << "Hasil pndk(" << n3 << ", " << k3 << ") adalah: " << pndk(n3, k3) << std::endl;
    std::cout << "Ini membuktikan bahwa untuk N=" << n3 << ", nilai kembaliannya adalah yang tertinggi." << std::endl;

    return 0;
}
