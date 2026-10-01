# NodeMCU manual 

## Benodigdheden 
Voor dit project heb je een aantal dingen nodig: 
- NodeMCU ESP8266
- Arduino IDE
- Telegram account
- Wifi verbinding
- Neopixel LED-strip
- USB-kabel

### Stap 1: Telegram installeren 
Installeer telegram via de App Store en maak een account aan. Voeg de user 'BotFather' toe. Dat kan je doen door de username in de zoekbalk te typen. Het kan zijn dat bij het opzoeken van dit account je meerdere BotFathers ziet verschijnen. Voeg alleen het geverifieerde account toe.

<img width="400" alt="IMG_8600" src="https://github.com/user-attachments/assets/d7b55900-7706-464a-a743-8f347234fd6b" />

Volg de stappen in het bericht en maak een nieuwe bot aan. Geef die een naam. Als het goed is heb je een token ontvangen. Die hebben we later nodig. LET OP! Deel deze token niet openbaar, iedereen kan je bot ermee besturen.

### Stap 2: Libraries installeren 
Voeg via de library manager in Arduino IDE ‘universaltelegrambot’ toe. Voeg ook de 'ArduinoJson' toe van Benoit Blanchen. 
<img width="207" height="183" alt="Scherm­afbeelding 2026-10-01 om 00 11 23" src="https://github.com/user-attachments/assets/6844e3cf-a947-4b2a-b33b-888434a45080" />
<img width="210" height="206" alt="Scherm­afbeelding 2026-10-01 om 00 10 14" src="https://github.com/user-attachments/assets/2b6fba82-e0a1-4ae1-baa7-4032e1ef295b" />

### Stap 3: Echobot openen 
Open 'echobot' uit universaltelegrambot. Doe dit stap voor stap: 
- file
- examples
- scroll naar beneden
- UniversalTelegramBot
- ESP8266 > EchoBot
<img width="701" height="354" alt="Scherm­afbeelding 2026-10-01 om 01 14 41" src="https://github.com/user-attachments/assets/00762ecc-aa67-43ca-ad82-f8ececeea15a" />

### Stap 4: Wifi
Vul nu de wifi in en de token die je eerder had opgehaald. Mocht je op school zijn, dan is het belangrijk om te weten dat de schoolwifi niet werkt op de NodeMCU. Gebruik daarom je hotspot. 

<img width="515" height="119" alt="Scherm­afbeelding 2026-10-01 om 01 21 03" src="https://github.com/user-attachments/assets/c722d7f1-3017-485b-a5c0-8a224a5f5634" />

### Stap 5: Uploaden
Sluit je NodeMCU aan op je laptop en upload de code. Controleer of je de juiste board hebt gekozen. Dat is de usbserial-310 of iets gelijks daar aan.

<img width="258" height="261" alt="Scherm­afbeelding 2026-10-01 om 02 35 05" src="https://github.com/user-attachments/assets/18a9095f-4b4b-4998-8f2d-78a699f93ca0" />

Open de serial monitor en zorg ervoor dat de baudrate op 115200 staat. Zo staat hij gelijk aan de waarde in de code Serial.begin(115200);
In de serial monitor kan je zien of je verbonden bent met het internet. 

<img width="354" height="86" alt="Scherm­afbeelding 2026-10-01 om 02 36 49" src="https://github.com/user-attachments/assets/18663153-324d-499f-891f-f0b93aca8109" />

### Stap 6: Echobot testen
Als je verbonden bent met het internet dan kan je testen of de bot werkt. Typ iets in de chat in telegram. Als je de zelfde response terugkrijgt, dan werkt het. In de serial monitor krijg je 'got response' te zien. 

<img width="500" alt="Scherm­afbeelding 2026-10-01 om 02 40 58" src="https://github.com/user-attachments/assets/998c2df0-ab91-424a-b75e-e051fa978a38" />

<img width="200" alt="Scherm­afbeelding 2026-10-01 om 02 41 12" src="https://github.com/user-attachments/assets/5de9f590-7e21-4548-b6f7-81fe1e7841b2" />

### Stap 7: Text weergeven 
Als je nu een bericht stuurt via telegram, zie je alleen 'got response' in de monitor. Dit gaan we aanpassen. 
Zet binnen de for-loop dit stuk code: 
bot.sendMessage(bot.messages[i].chat_id, bot.messages[i].text, ""); 

Nu kan je ook zien wat voor berichten er worden gestuurd via telegram. 
 
<img width="546" height="89" alt="Scherm­afbeelding 2026-10-01 om 11 35 10" src="https://github.com/user-attachments/assets/202313ff-7357-44ea-9f32-3e372523bc13" />

We kunnen ook een antwoord terug versturen, in plaats van dat de automatische response een echo is. 
Plak in de zelfde for-loop dit stukje en vul zelf jouw response in: 
bot.sendMessage(bot.messages[i].chat_id, "xxjouwtekstxx", ""); 

<img width="734" height="73" alt="Scherm­afbeelding 2026-10-01 om 11 41 17" src="https://github.com/user-attachments/assets/82217115-b4db-4505-b84d-8d1d641dc152" />





## Troubeshooting

#### 'Not Connected'
Mocht je in je serial monitor deze error te zien krijgen, dan betekend het dat je NodeMCU niet goed verbonden is. Doe de USB kabel opnieuw in je laptop en ook in je NodeMCU, het kan zijn dat hij los zat of niet goed aangesloten was. 


<img width="724" height="48" alt="Scherm­afbeelding 2026-10-01 om 02 45 13" src="https://github.com/user-attachments/assets/5702aa64-3380-4d04-b845-dd8a0727375f" />

#### Onwijs veel stipjes
Zie je bij het verbinden vage tekens en veel stipjes? Dat betekend dat er wordt geprobeerd om te verbinden met het internet. 
Check of de wifi naam en code wel kloppen en upload de code opnieuw. 
Lukt het niet? Sluit je laptop dan aan op je hotspot en vul die gegevens in de code. 

<img width="945" height="35" alt="Scherm­afbeelding 2026-10-01 om 02 49 38" src="https://github.com/user-attachments/assets/e465031a-0d56-45cd-b7ec-99328a8bc611" />

#### Geen response in de serial monitor 
Zie je wel de echo op telegram, maar geen response terug in de monitor? Check dan of de baudrate wel klopt. De baudrate moet altijd gelijk staan aan de cijfers in de code. In dit geval 115200. 

#### 'No such file'
Ontvang je een error met 'no such file'? Dat betekend dat de library ontbreekt. Ga terug naar de Library Manager en controleer of alles goed gedownload is, en ook de juiste versie. 


#### Compilation error
Heb je de code geplakt in Arduino maar krijg je een compilation error? Dat betekend dat de regel niet op de goede plek staat. Controleer of hij echt in de for-loop staat. 

<img width="400" alt="Scherm­afbeelding 2026-10-01 om 11 42 09" src="https://github.com/user-attachments/assets/d89504c7-568e-443c-9026-78b907fbe76c" />

### Mijn eigen probleem
Ik had niet zoveel problemen met de opdracht, tot ik de led aan moest sluiten. Ik probeerde de stappen te volgen en een loop te maken, maar er werd alleen gereageerd op het disco stukje, en niet op de: 
 if (bot.messages[i].text == "lights on")
{
  digitalWrite(LED_BUILTIN, LOW);
Ik heb geprobeerd om de HIGH en LOW te wisselen, maar dat hielp ook niet. 
Daarom heb ik ChatGPT ingeschakeld. Die had geholpen met de code en die werkte uiteindelijk wel. Die code werkte wel, maar ik vond hem ingewikkeld. Daarom heb ik ervoor gekozen om hem niet verder in de handleiding te verwerken, omdat ik het zelf ook niet helemaal snap. 

Bron: https://chatgpt.com/share/6abe37bf-6f24-83eb-ae07-691cd25051c3
  
  



