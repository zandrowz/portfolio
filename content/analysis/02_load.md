---
Title: Load
Description: Load.
Template: analys
---

Load
=======================

<!-- Skriv en eller två rader om vad uppgiften handlar om. -->
I denna rapport ska jag analysera tre webbplatsers laddningstid, i mobil och dator, samt presentera och analysera resultatet.

Urval
-----------------------

<!-- Berätta vilka webbplatser du valt att undersöka och varför eller hur du gick tillväga när du gjorde ditt urval. -->
Jag har valt att analysera tre webbplatser som inriktar sig på försäljning av hemelektronik. 
E-handeln ökar för varje år och detsamma gäller även antal e-handelsföretag. Därför valde jag att jämföra tre av de stora hemelektronikskedjornas webbplatser, för att se hur de klarar sig i ett jämförelsetest av deras webbplatser laddningstid. Jag valde dessa tre: Dustinhome, MediaMarkt och Elgiganten, som hamnar i topp i en googlesökning på hemelektronik.

Metod
-----------------------

<!-- Berätta kort om din "metod", hur du gör för att utföra undersökningen. Berätta om du använder något speciellt verktyg. -->
För att mäta webbplatsernas laddningstid har jag använt mig av Pagespeed Insights(PSI) som används för att mäta webbplatsers prestanda. Google ger ett betyg på webbplatsen och rekommendationer om hur webbplatsen kan förbättra sin prestanda.
Jag har även för varje sida använt mig av devtools flik networks för att se sidornas totala laddningstid tillsammans med antalet resurser som laddas samt sidans totala storlek.
Resultaten från alla mätningar har jag sparat i ett excel-ark som går att se under "Resultat" nedan.

Resultat
-----------------------

<!-- Dokumentera dina resultat från din studie. Berätta vad du kom fram till, vilka resultat du hittade och observerade. -->
Alla mätningar har gjorts tre gånger för att få fram snittet för mätningarna. Alla tester har gjorts på samma dator.
<b>För kännedom så kan resultetet från mina mätningar inte visa ett fullt rättvisst resultat då mätningarna utfördes vid en dator som begränsas av en pfSense brandvägg, som filtrerar bort en del av innehållet på sidorna. Det kan göra att mitt resultat för antal resurser som används visar mindre än vad det är egentligen.</b>

<b>Mätningar från samtliga webbplatser</b><br>
<div class="embed-container2">
<iframe src="https://docs.google.com/spreadsheets/d/e/2PACX-1vR3sy9CTP198xLHg_B3D3mmoEjuqgyVhLfbBu0nJfqpQGtS-W_4sdOP1Uo4SQI_FQsf-hjLjNGmbLPs/pubhtml?widget=true&amp;headers=false"></iframe>
</div>

<b>Dustinhome</b><br>

https://www.dustinhome.se/
![dustinhome](%assets_url%/img/dustin.png)
Som kan läsas i tabellen ovan får Dustinhomes startsida 55/100 i prestandabetyg och godkänt i testet av viktiga webbvärden av PSI. Deras mobila version får endast 11/100 i prestanda och får inte godkänt i något test. Time to interact är 26,2s på den mobila versionen vilket är högt, på dator visar den 5,5s.
De behöver minska körningstiden för JavaScript rejält och ta bort resurser som blockerar renderingen för att få ner laddningstiden för sidan. Det gäller även desktop versionen som även den behöver minska sin javascript kod och även ändra på deras bildformat genom att använda modernare bilfdormat som WebP och AVIF istället för PNG eller JPG. 

<b>MediaMarkt</b><br>

https://www.mediamarkt.se/
![mediamarkt](%assets_url%/img/mediamarkt.png)
MediaMarkt får underkänt i båda testerna av PSI och får låga betyg i båda, 23/100 i dator och 20/100 på mobil och får inte godkänt. Time to interact visar 29,0s på mobil och 6,4s i mobilen, vilket drar ner resultatet. De har inte lyckats med att ta bort sin css/javascriptkod som blockerar renderingen och eliminera oönskade resurser. 

<b>Elgiganten</b><br>

https://www.elgiganten.se/
![elgiganten](%assets_url%/img/elgiganten.png)
Elgiganten klarar sig bättre i testerna och får 85/100 i dator och 53/100 i mobil, men den mobila versionen får inte godkänt av PSI i test av viktiga webbvärden. I sin mobila version är de mindre bra på att reducera javascript/css och testerna visar även att de behöver minska på serverns första svartid. Desktop versionen klarar sig bra men har inte lyckats med att ta bort resurser som blockerar renderingen, dvs. laddningsordningen på sidan t.ex. hur Javascript och CSS-kommandon läses in.


Analys
-----------------------

<!-- Diskutera och analysera de resultaten du fann. -->
Testerna visar att alla tre sidor har liknande saker de behöver förbättra och ingen klarar sig fullt ut i testerna. I alla tester så klarar sig desktop versionerna sig bättre än för mobilen, både vad gäller laddningstider och prestanda. Eftersom kategorin på mitt val av urval av webbplatser är e-handel, som ofta förknippas med säljande bilder och massor av reklam, så tycker jag ändå att alla sidor klarar sig ganska bra. Gemensamt för alla är att de behöver reducera javascript/css som inte används vilket man kan se vid mätningen med devtools - att alla webbplatser innehåller mycket javascript. I Dustinhomes fall behöver de ändra sitt format på bilderna och genom att ange storlek på sina bilder skulle det kunna snabba upp sidan. 

MediaMarkts webbplats får väldigt dåligt betyg i mätning av 'Cumulative Layout Shift' (CLS), dvs att när en webbsida ”hoppar till” någon eller ett par sekunder efter att den först renderats, vilket gör att man t.ex. kan råka trycka på fel knapp på sidan eller liknande. Detta drar ner betyget på deras sidor.

Som jag skrev ovan så filtreras en del av innehållet bort på datorn jag gjort testerna på, pga av en pfSense brandvägg, så laddningstiden blir lite kortare än vad den skulle vara i normala fall. Men man kan ändå se att alla tre sidor har relativt bra laddningstid trots sitt innehåll med mycket javascript och reklam. Ett utmärkande exempel är ju Elgigantens undersida 'veckan kampanjer' som innehåller 56 MB data med mycket bilder och youtube-klipp vilket drar ner på laddningstiden. Där skulle de kunna minska på datan och förbättra laddningstiden.

Vid val av vinnare av testen stod det mellan MediaMarkt och Elgiganten. MediaMarkt har lite bättre laddningstider men Elgiganten lyckas mycket bättre i PageSpeed Insights tester så jag utser Elgiganten till vinnare. 
En laddningstid under två sekunder tycker jag är okej. Men just laddningstiden är inte jätteviktig för mig utan jag är mer för att resten av webbplatsen fungerar som den ska. Jag provad även alla sidors laddningstid på en äldre bärbar dator med trådlöst nätverk och då var laddningstiderna avsevärt mycket högre. Så mycket handlar ju om vilken dator och vilket nätverk man använder.


Referenser
-----------------------

<!-- Ange de eventuella referenser du använder dig av, om några. -->

- Google Pagespeed Insights (https://pagespeed.web.dev/)
- Mozilla Firefox Devtools
- Dustinhome (https://www.dustinhome.se/)
- MediaMarkt (https://www.mediamarkt.se/)
- Elgiganten (https://www.elgiganten.se/)

Övrigt
-----------------------

Sandra Karlsson
