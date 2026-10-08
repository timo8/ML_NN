# Strojové učenie a neurónové siete

## Úvod

Repozitár obsahuje vypracované zadania z predmetu **Strojové učenie a neurónové siete (SUNS)**. Jednotlivé zadania sa venovali rôznym oblastiam strojového učenia a neurónových sietí – od analýzy a predspracovania dát, cez klasické klasifikačné algoritmy až po konvolučné neurónové siete a transfer learning.

Počas riešenia zadaní sme sa venovali najmä predspracovaniu dát, experimentovaniu s parametrami modelov, porovnávaniu rôznych metód a vyhodnocovaniu ich výsledkov.

## Zadanie 1 – Klasifikácia počasia

Cieľom zadania bolo vytvoriť model schopný klasifikovať počasie do 4 kategórií: **Sunny, Cloudy, Rainy a Snowy**.

Dataset `weather_data.csv` obsahuje údaje o počasí, ako napríklad teplota, vlhkosť, rýchlosť vetra, oblačnosť, atmosférický tlak a ďalšie charakteristiky.

### Predspracovanie dát

Pred trénovaním modelov bolo potrebné dáta upraviť. Odstraňovali sme chýbajúce hodnoty (`NULL`, `NaN`) a spracovávali outliery. Nečíselné atribúty boli prevedené na číselnú reprezentáciu pomocou **label encodingu**.

Numerické atribúty boli následne škálované, aby mali porovnateľný rozsah a aby sa zlepšila stabilita a konvergencia modelov.

<img width="847" height="545" alt="image" src="https://github.com/user-attachments/assets/07ee8164-b2ef-4191-8d8e-64ba0b918150" />


### Logistická regresia

Ako jeden z klasifikačných modelov sme použili **logistickú regresiu** na predikciu jednej zo štyroch kategórií počasia.

Pri modeli sme experimentovali s rôznymi nastaveniami a sledovali ich vplyv na výslednú úspešnosť klasifikácie. Výsledky logistickej regresie zároveň poskytli základ na porovnanie s neurónovou sieťou.

### Exploratory Data Analysis

Venovali sme sa aj exploratívnej analýze dát (EDA), ktorej cieľom bolo lepšie pochopiť vlastnosti datasetu a vzťahy medzi jednotlivými atribútmi. Analyzovali sme rozdelenie hodnôt, chýbajúce údaje a vzájomné závislosti medzi premennými.

Pomocou vizualizácií sme sledovali napríklad vzťah medzi **teplotou a vlhkosťou v jednotlivých ročných obdobiach**, rozdelenie jednotlivých kategórií počasia a ďalšie súvislosti v dátach.

<img width="847" height="545" alt="image" src="https://github.com/user-attachments/assets/4919009f-3e31-4750-8575-1277e154a989" />


### Neurónová sieť

V závere zadania sme vytvorili a trénovali neurónovú sieť určenú na klasifikáciu počasia. Experimentovali sme s rôznymi hyperparametrami a sledovali priebeh učenia modelu.

Pri trénovaní sme využili aj **early stopping**, ktorý umožňuje ukončiť trénovanie v prípade, že sa výkon modelu na validačných dátach prestane zlepšovať.

<img width="1389" height="490" alt="image" src="https://github.com/user-attachments/assets/379914b6-9c67-4368-bf71-1c871306e3c6" />

<img width="654" height="590" alt="image" src="https://github.com/user-attachments/assets/31edfd3b-d638-4bb7-959c-4e933a53b20b" />


---

## Zadanie 2 – Stromy, stroje, hlasovania a redukcia dimenzie

Druhé zadanie bolo zamerané na **regresiu a predikciu ceny leteniek**. Pracovali sme s datasetom letov, pričom cieľovou premennou bola `Price`.

V prvej časti sme sa venovali príprave dát pre modely strojového učenia. Odstraňovali sme nepotrebné identifikačné atribúty, chýbajúce hodnoty, duplikáty a outliery.
Textové atribúty sme prevádzali do číselnej podoby pomocou vhodných metód kódovania a vstupné údaje sme následne normalizovali.

<img width="870" height="545" alt="image" src="https://github.com/user-attachments/assets/91847e56-aca9-4185-bf95-6bb57f978af3" />


### Regresné modely

Na predikciu ceny leteniek sme použili viacero regresných modelov:

- **Decision Tree Regressor**
- **Random Forest Regressor**
- **Support Vector Regression (SVR)**

Pri jednotlivých modeloch sme experimentovali s ich parametrami a porovnávali ich výsledky. Modely sme vyhodnocovali pomocou metrík **MSE, RMSE a R²** a zároveň sme analyzovali reziduály.

<img width="1389" height="590" alt="image" src="https://github.com/user-attachments/assets/b668b1d4-4cac-4b71-8017-5cd0d569a37c" />

Pri ensemble modeli sme sa venovali aj **dôležitosti vstupných atribútov**, pomocou ktorej sme sledovali, ktoré vlastnosti datasetu mali najväčší vplyv na predikciu ceny.

<img width="921" height="545" alt="image" src="https://github.com/user-attachments/assets/4695a6d9-d0b2-4f8a-9400-619cdbbe6504" />


### Redukcia dimenzie

Ďalšia časť zadania bola zameraná na vizualizáciu a redukciu dimenzie dát. Najskôr sme vybrali tri pôvodné atribúty a pomocou 3D scatter grafu sledovali ich vzťah k výslednej cene letenky.

<img width="781" height="656" alt="image" src="https://github.com/user-attachments/assets/2afb2faf-d046-46e7-a8f3-6d37b888ff71" />


Následne sme pomocou **PCA (Principal Component Analysis)** zredukovali normalizované vstupné dáta na tri dimenzie a výsledok sme porovnali s pôvodnou reprezentáciou dát.

<img width="781" height="656" alt="image" src="https://github.com/user-attachments/assets/da34f840-548d-4154-a844-1885df91e52e" />


### Výber atribútov

V závere sme skúmali vplyv redukcie počtu vstupných atribútov na kvalitu výsledného modelu. Najúspešnejší model z predchádzajúcej časti sme opätovne natrénovali s podmnožinami atribútov vybranými:

- podľa korelačnej matice,
- podľa dôležitosti atribútov z ensemble modelu,
- podľa vysvetlenej variancie pomocou PCA.

Výsledky jednotlivých prístupov sme následne porovnávali s pôvodným modelom pomocou metrík **MSE, RMSE a R²** a pomocou analýzy reziduálov.

<img width="714" height="436" alt="image" src="https://github.com/user-attachments/assets/b11c1cc3-9fec-4db5-9112-a5c17e5e71af" />

---

## Zadanie 3 – Konvolučné neurónové siete a obrazová klasifikácia

Tretie zadanie bolo zamerané na **klasifikáciu obrazov pomocou konvolučných neurónových sietí (CNN)**. Pracovali sme s datasetom približne 7 800 obrázkov, ktoré reprezentovali približne **200 druhov vtákov**. Obrázky boli spracovávané vo všetkých troch farebných kanáloch RGB.

### Predspracovanie dát

Pre trénovaciu, validačnú a testovaciu množinu sme pripravili samostatné generátory. Obrázky boli pri načítavaní zmenšené na rozlíšenie **64 × 64 pixelov**, čím sa znížila pamäťová a výpočtová náročnosť trénovania.

Hodnoty pixelov boli zároveň normalizované z pôvodného rozsahu 0–255 do rozsahu **0–1**. Pri trénovacej množine sme využili aj náhodné miešanie (`shuffle`), aby sa model nemohol učiť poradie obrázkov v datasete.

### Vlastná konvolučná neurónová sieť

Vytvorili sme vlastnú konvolučnú neurónovú sieť pozostávajúcu z **troch konvolučných vrstiev**. Na obmedzenie pretrénovania a zlepšenie procesu učenia sme využili viacero regularizačných techník, napríklad:

- **Dropout**,
- **L2 regularizáciu**,
- **Batch Normalization**,
- **Early Stopping**.

V rámci experimentov sme skúšali rôzne konfigurácie hyperparametrov, napríklad počet filtrov, typ poolingu a veľkosť pooling filtra. Jednotlivé konfigurácie sme následne porovnávali podľa dosiahnutej úspešnosti.

### Transfer Learning

Na ďalšie spracovanie sme využili predtrénovanú sieť **MobileNetV2**, ktorá bola použitá na generovanie príznakov z obrázkov. Namiesto výslednej triedy tak sieť poskytla vektor príznakov reprezentujúci vlastnosti daného obrázka.

Vygenerované príznaky sme spolu s cestou k obrázku a príslušnou triedou uložili do DataFrame pre jednotlivé dátové množiny.

### Zhlukovanie príznakov

Pred samotným zhlukovaním sme pomocou **PCA** zredukovali počet dimenzií získaných príznakov na 15. Následne sme použili algoritmus **K-Means**, ktorý rozdelil obrázky do zhlukov na základe podobnosti ich príznakov.

Pre jednotlivé zhluky sme analyzovali zastúpené obrázky a priemerné obrázky zhlukov. Na základe vizualizácií sme sa snažili určiť, aké spoločné vlastnosti majú obrázky patriace do jednotlivých zhlukov, napríklad podobné sfarbenie vtákov alebo podobné pozadie.

### Klasifikácia pomocou SVM

Na príznakoch získaných pomocou MobileNetV2 sme následne trénovali **Support Vector Machine (SVM)** klasifikátor. Výsledky sme porovnávali s vlastnou konvolučnou neurónovou sieťou a analyzovali sme úspešnosť klasifikácie a chyby jednotlivých modelov.

SVM sme zároveň využili aj na klasifikáciu vytvorených zhlukov, pričom sme sledovali rozdiely v úspešnosti medzi jednotlivými zhlukmi a analyzovali možné príčiny týchto rozdielov.
