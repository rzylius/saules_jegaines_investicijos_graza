# saules_jegaines_investicijos_graza
Saulės jėgainės namų ūkiui investicijų gražos skaičiavimas.

Asmeninės saulės jėgainės reklaminiai skaičiavimai yra išpūstai nerealistiniai, neatspindintys tikros finansinės naudos.

Čia bandymas sukurti modelį, kuris atspindėtų kai kuriuos praktinius netikrumus. Suprantama, modelis netobulas, bet tikiuosi bus kiek naudingesnis nei paprastieji pardaviminiai montuotojų paskaičiavimai.

Įdomu išgirsti jūsų pastebėjimus ir pamastymus, kaip iš tikro turėtume vertinti, kokius aspektus įskaičiuoti į tokį modelį. Komentuokite, rašykite pastebėjimus, padarykime geresnį modelį.

Svarbu turėti omeny, kad saulės elementų amžius ilgas, tačiau inverterio darbo laikas ribotas. Šiame modelyjė nėra įdėtas inverterio eitimas - remontas, turbūt būtų prasminga planuoti naujo inverterio kaštus bent jau po penkiolikos metų darbo.

Reguliatoriaus strategija dėl "pasaugojimo" kainos yra neaiški ir gali keistis neprognozuojamai. Tad čia dar vienas ženklus netikrumas.


Kai kurie paaiškinimai:

# "Teorinė gamyba įvertinant 1% efektyvumo praradimą per metus (kWh/metai)"
- nuo penktų metų įskaičiuotas 1 procento efektyvumo mažėjimas. Pasireguliuokite pagal konkrečius elementus.

# "Elementų efektyvumas" 
yra tik išvestinis dydis, skaičiuojamas iš ankstesnio stulpelio duomenų. Tad jis tik pademonstravimui efektyvumo, jo nereikia liesti.

# "Atsitiktinis produkcijos svyravimo dydis (-20 iki +20%)"
faktiškai sugeneruotas elektros kiekis per mestus priklausys nuo oro sąlygų ir, anot praktikų, gali kisti +- 20 procentų. Tad modeliuojame šiame stulpelyje atsitiktinį svyravimą plius minus 20 proc. Excelio yoatybė - šie atsitiktiniai skaičiai persiskaičiuoja kiekvieną kartą, kai ką nors pakeičiate lentelėje, ar paspaudžiate "recalculate".

# "Sugeneruotas el. kiekis, kWh" 
suskaičiuojamas faktinis sugeneruotas kiekis (t.y teorinė gamyba plius atsitiktinė +-20 proc".

# "Realus energijos poreikis kWh per metus"
čia jūsų naudojamas elektros kiekis, jei neturėtumėt saulės jėgainės. Šis skaičius labai svarbus pajusti realius taupymus. Kadangi su saulės jėgaine pereiname nuo "kintamųjų kaštų" (kai mokame už kiekvieną kkwh) prie pastoviųjų kaštų - kai ~30 metų sumokėjome už visas pagamintas kwh, tai pasikeis ir vartojima paternas. 

Dėl dabartinio reguliavimo gaminti per daug neapsimoka, nes nesunaudota energija yra nusavinama. Gaminti per mažai irgi neapsimoka, nes už papildomą energiją yra mokama vieno tarifo skaitikliu. (abu šie dalykai turėtų ilgainiui pasikeisti, nes įstatymo pataisos priimtos ir ESO žada pokyčius).

Todėl gaunasi, kad efektyviausiai išnaudojant jėgainę reikia sunaudoti visą energiją kiek jos pagamini, net jei tau jos nereikia. Mano nuomone tai absurdiška, ir tikrasis BASELINE atsipirkimo scenarijus yra "kiek būčiau išleidęs pinigų elektrai pirkti, jei nebūčiau statęs jėgainės", t.y. gyvendamas komfortabiliai ir normaliai taupęs.

Parametras nustatomas langelio "Metinis suvartojimo didejimas" keitimu. Reikia turėti omeny, kad jei planuojate kažkada elektromobilį, tai nuo tų metų turite pridėti ~4-5 tūkstančius kwh prie savo vartojimo.


# "Sunaudota energija viduje (kWh)"
sunaudotas energijos kiekis momentiškai, t.y. nepriduodant į tinklą. Namų automatizavimas, smart grid įrenginiai, elektrinis vandens šildymas pertekline energija, baterijos, tie įrenginiai didina momentinį vartojimą.  Parametras nustatomaskeičiant laukelį " % energijos suvartojamas tiesiogiai, nesaugant tinkle" arba tiesiogiai langeliuose.

Kiek matau iš diskusijų, dėl nevienodo fazių apkrovimo net jei gamianme dieną daug elektros gali būti, kad tuo pačiu ją naudojame. T.y. viena fazė yra apkrauta per daug, todėl jai saulės neužtenka, o kitos fazės tiekia energiją į tinklą. Tokiu atveju inverteris balansuojantis fazes papildomai padidins momentinį vartojimą.

# "Į tinklą priduotos energijos kiekis, kWh"
nesunaudotos energijos kiekis priduotas į tinklą.

# "Energijos balansas (sugeneruota - suvartota) kWh" 
tai faktiškai sugeneruotas kwh minus realus sunaudojimas. Jei skaičius teigiamas, reiškia tiek kwh padovanojau. Jei neigiamas, tiek turėjau dapirkti.

# "Reikalingos energijos dapirkimas, EUR"
kiek EUR kainavo dapirktos kwh

# Vidutinė dabar naudojamos el. kaina (ct)
Kadangi dabar dažniausiai didesnis elektros vartotojas naudojasi dviejų laikų skaitliuku (o tapus gaminančiu-vartotoju bus pervestas į vieno tarifo skaitliuką), tai šiame stulpelyje rašome dabar faktinę naudojamos elektros kwh kainą (išvestas iš to kiek naudojate vidutiniškai dienos ir nakties). Jei turite vieno tarifo skaitiklį, tai čia bus tiesiog vieno to tarifo kwh kaina

# Vienos fazės energijos kaina(ct)
vieno tarifo kwh kaina, į kurį ir būsite pervesti

# SCENARIJAI
Scenarijuose turime du stulpelius - metų stulpelį (be spalvos) ir akumuliuotą stulpelį (spalvotas). Akumuliuotas rodo suminį taupymą ir yra raudonas iki taupymai viršija investuotą į jėgainę sumą.


# BASELINE: 
kiek būčiau išleidęs elektrai, jei nebūčiau pirkęs jėgainės

# OPTIMISTINIS PARDAVIMINIS: 
Teorinis atsipirkimas: kiek sutaupyčiau, jei neturėdamas jėgainės būčiau pirkęs visą savo jėgainės gaminamą elektros kiekį	

# Hardcore atsipirkimas I: 
elektros kaina kurią būčiau mokėjęs be elektrinės minus pasaugojimo kaina, minus papildomai pirktos  elektros kaina. Pasaugojimas apmokamas centais

# Hardcore atsipirkimas II: 
elektros kaina kurią būčiau mokėjęs be elektrinės minus pasaugojimo kaina, minus papildomai pirktos  elektros kaina. Pasaugojimas apmokamas kilovatvalandėmis.


Fiksuotos pasaugojimo kainos scenarijaus nedėjau.


# INTERNAL RATE OF RETURN investicijai skaičiavimas
investicijų gražos skaičiavimas, čia rasite atskirame worksheet'e







