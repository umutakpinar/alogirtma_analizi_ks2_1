
# Algortima Analizi ve Tasarımı KS-2

Verilen kod, bazı işlemler ve algoritmaları içeren bir programı temsil etmektedir. Kodda kullanılan işlemler arasında dizi oluşturma, dizi sıralama, toplam hesaplama, graf matrisleriyle işlemler yapma ve sonuçları yazdırma gibi işlemler yer almaktadır.

Fonksiyonların gerçeklediği işlemleri ve kodu kısaca inceleyelim.

#include <stdio.h>: G/Ç kütüphanesini import eder.
#include <stdlib.h>: Standart kütüphane işlemlerini impoert eder.
#include <time.h>: Zaman işlemleri için gerekli kütüphaneyi import eder.
#include <limits.h>: Veri tipi sınırlarını (limitlerini) barındıran kütüphaneyi import eder.


Başlangıçta bir dizi ve bir graf matrisi tanımlanır.

#define A_SIZE 20: A_SIZE adında bir sabit oluşturur ve 20 değerini atar.
#define G_SIZE 10: G_SIZE adında bir sabit oluşturur ve 20 değerini atar.
#define MAX_W 10: MAX_W adında bir sabit oluşturur ve 10 değerini atar.
#define INF INT_MAX: INF adında bir sabit oluşturur ve Integer veri tipinin maksimum değerini atar.

generate fonksiyonu, parametre olarak bir a dizisi ve boyut (size) alır. Bir döngü ile rand fonksiyonunu kullanarak bir rastgele sayı üretir. Bu rastgele sayı, -MAX_W ve MAX_W sabiti arasında bir değere sınırlandırılır ve dizinin ilgili elemanına atanır. 

function1 fonksiyonu, sıralama algoritması kullanarak diziyi küçükten büyüğe doğru sıralar (kodda Bubble Sort kullanılmış). Burada BubbleSort yerine QuickSort gibi daha düşük zaman karmaşıklığına O(nlogn) sahip bir sıralama algoritması kullanılabilirdi.

function2 fonksiyonu, bir dizi üzerinde döngü kullanarak alt dizilerin toplamlarını hesaplar. Her adımda, bir eleman eklenerek alt dizinin toplamı güncellenir. Eğer alt dizinin toplamı 0'dan küçük bir değer alıyorsa, alt dizi sıfırlanır ve toplam sıfırlanır. Bu sayede, alt dizilerdeki negatif toplamlar atlanarak en büyük toplama ulaşılır. Bu fonkisyonda genel geçer bilinen bir toplama algoritması kullanılmamış.

function3 fonksiyonu, graf matrisleriyle çalışarak en kısa yol problemini çözer (Floyd-Warshall algoritması kullanılmış). fonksiyonu, girdi olarak bir ağırlık matrisi (g) ve boş bir mesafe matrisi (d) alır. Bu fonksiyon, Floyd-Warshall algoritmasını kullanarak girdi ağırlık matrisine dayalı olarak en kısa yol mesafelerini hesaplar ve mesafe matrisine kaydeder.

Floyd-Warshall algoritması, dinamik programlama yaklaşımını kullanır ve tüm çiftler arasındaki en kısa yol mesafelerini bulmak için çoklu geçişler yapar. Burada algoritma, üçlü bir döngü kullanarak O(n^3) tüm düğümler üzerinden geçerek her bir ikili düğüm arasındaki en kısa yolu günceller.

Başlangıçta mnesafe matirisini sıfır veya sonsuza set eder daha sonra k döngüsü ile her düğüm üzerinden geçerek i ve j döngüsü ile tüm düğümler arasındaki en kısa yol mesafelerini günceller. Yani mesafe mevcut mesafeden küçükse, yeni değer ile güncellenir.
Sonuçta d matrisi en kısa yol değerlerini içerecek şekilde güncellenmiş olur. Ben burada Floyd-Marshall yerine Djikstra ve Bellman-Ford algoritmalarını denedim ancak kodun derlenme süresi açısından elde ettiğim en iyi sonuç halilhazırda kullanılan Floyd-Marshall ile oldu. Test cihazım güncel bir işlemciye sahip olduğu için aslında değerler birbirine çok yakın çıktı bu nedenle testi bir de Online Compiler üzerinde yaptım. Burada Floyd-Marshall çok daha iyi sonuçlar verdi. Bu nedenle function3'ü yeniden revize etmenin bir anlamı olmadığını düşünüyorum. Yine de function3 altında diğer iki algoritmayı da function3'e uygulayarak yorum satırı olarak ekledim.


print1, print2 ve print3 fonksiyonları, dizileri veya matrisleri ekrana yazdırmak için kullanılmış.

main fonksiyonu, diğer fonksiyonları sırasıyla çağırarak programın işlemleri sırasıyla gerçekleştirmesi için kullanılmış.

Özetle bu program, bir dizi üzerinde sıralama işlemi yapar, belirli bir kurala göre bir toplam hesaplar ve graf matrisleriyle en kısa yol problemini çözer. Programın çıktısı, yapılan işlemlerin sonuçlarını ekrana yazdırır.


Kodu zaman karmaşıklığı açısından incelediğimde O(n^3) olduğunu gördüm. 
generate fonksiyonu: O(n) zaman karmaşıklığına sahiptir, çünkü n adet rastgele sayı üretiyor.
function1 fonksiyonu: Bubble sort algoritmasını kullanıyor ve Average case durumunda da genellikle O(n^2) zaman karmaşıklığına sahip. Ancak araştırdığım kaynaklara göre anladığım kadarıyla bazı optimizasyonlar uygulayarak bu algoritmanın O(n) duruma da sahip olduğu durumlar olabiliyormuş.
function2 fonksiyonuna bakacak olursak O(n) zaman karmaşıklığına sahip, çünkü bir döngü aracılığıyla diziyi tek seferde tarıyor ve en büyük toplam değeri hesaplıyor.
function3 fonksiyonu yukarıda da bahsettiğim üzere Floyd-Warshall algoritmasını kullanmakta ve O(n^3) zaman karmaşıklığına sahip. İki adet üçlü döngü içeren bu algotritma matris boyutu n olduğunda üçgen matristeki her bir hücreyi gezmek için n^3 adım atıyor. Böylece toplam karmaşıklığı göz önüne alırsak bu kod O(n^3) zaman karmaşıklığına sahip olmuş oluyor.

Kodun iyileştirilmesi için yapılabilecekler hususunda ise yukarıda da bahsettiğim üzere
function1 için Quick Sort gibi daha verimli bir sıralama algoritması kullanılabilir. Quick Sort, average case durumda O(n log n) zaman karmaşıklığına sahip bu nedenle bubble sort'a göre daha hızlı çalışabilir.
function2 zaten O(n) zaman karmaşıklığına sahip, içerisinde özel bir algoritma kullanılmamış bu kısımda bir iyileştirme yapılabilir mi bilmiyorum.
function3 için Floyd-Warshall algoritmasının yerine, daha hızlı olabilecek Djikstra veya Bellman-Ford gibi bir algoritma kullanılabilir. Ancak test cihazımda ve Online Compiler'da fiziksel hıza bakılırsa Floyd-Marshall bende en iyi sonucu verdi. Elbette zaman karmaşıklığı ile fiziksel hızı karşılaştırmak doğru değil bu nedenle Floyd-Marhsall, Bellmann-Ford ve Djikstra algortimalarını zaman karmaşıklığı açısından kıyaslayalım :
Öncelikle bu kıyaslamada kullanacağımız sembolleri detaylanıralım.
"E" sembolü, algoritmalarda kullanılan kenar (edge) sayısını temsil eder. Dolayısıyla, E işareti "kenar sayısı" anlamına gelir. Algoritmalarda genellikle düğüm (vertex) sayısı "V" ve kenar sayısı "E" olarak temsil edilir. Örneğin, V düğüm ve E kenar sayısına sahip bir grafikte, algoritmanın zaman karmaşıklığı V ve E'ye bağlı olarak hesaplanır.

Dijkstra Algoritması:
Average Case: O((V + E) log V)

Bellman-Ford Algoritması:
Average Case: O(VE)

Floyd-Warshall Algoritması:
Average Case: O(V^3)

Zaman karmaşıklıklarına bakıldığında Bellman-Ford çok daha verimli gözüküyor. Bu durumda function3 içerisinde Bellman-Ford algoritmasının uygulanması düşünülebilir. Ancak araştırmalardan anladığım kadarıyla Floyd-Warshall algoritması genellikle daha küçük grafiklerde tercih ediliyor (verilen kod bloğu da buna bir örnek temsil edebilir). Bu nedenle burada bir iyileştirme yapılmasına gerek görmedim.

Bunlar dışında elbette bazı veri yapıları veya algoritma optimizasyonları da verilen kod bloğunda kullanılabilir. Örneğin, veri yapılarının veya döngülerin gereksiz tekrarlanması engellenebilir, geçici değişkenlerin azaltılması sağlanabilir veya gereksiz hesaplamalar önlenebilir.

Sonuç olarak ben yalnızca BubbleSort yerine QuickSort uygulanmasını uygun gördüm ancak QuickSort'Un uygulanması kodun genel toplamda zaman karmaşıklığını değiştirmiyor. Bu nedenle her iki kodun zaman karmaşıklığı aynı ve O(n^3) olacaktır. Çalışma süreleri de yine yukarıda değindiğim üzere kullandığım test cihazının güncel bir işlemciye sahip olmasından dolayı çok küçük farklar oluşturmakta.

Yine de orijinal kodu derlediğimde 0.000099 değerini elde ederken, QuickSort ile 0.000078 değerini elde ettim.

Recep Umut Akpınar 1190505805