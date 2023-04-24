![Overview](.\resources\Overview.jpg)

## The setup

EnOcean is a wireless communication protocol that allows low-power devices to communicate with each other without the need for batteries or wired connections. It is designed for use in energy-efficient buildings and smart homes, where sensors and control systems need to be able to communicate with each other wirelessly over long distances without consuming a lot of power.

EnOcean uses energy harvesting technology to power its devices. This means that the devices are able to capture energy from their environment, such as from light or motion, and use that energy to transmit data wirelessly. This eliminates the need for batteries or wired connections, making EnOcean devices easy to install and maintain.

EnOcean uses a unique data link layer protocol called "EnOcean Radio Protocol" (ERP) and uses a combination of frequency-shift keying (FSK) and amplitude-shift keying (ASK) modulation to transmit data. ERP is a packet-based protocol that consists of a  synchronization byte, header, data field, and optional fields such as security and CRC.

> BeckHoff Application Film: [Building Automation in a Miele administration building](https://youtu.be/4wDrKjwuDCw?t=164)

> Beckhoff Application Film: [Beckhoff manages 60K data points in Tower 185 at Frankfurt, consisting of DaLI and EnOcean communication.](https://www.youtube.com/watch?v=8wU_nKmCpQ0)

## Hardware

- EnOcean devices:
  - Eltako F4T65-wg, vier druktoetsen + QR11Gs-sz kader
  - Eltako FFT65B-wg, temperatuur en luchtvochtigheid sensor
  - Eltako FUD61NPN, universele dimactor
- PLC terminal: 
  - KL6581 EnOcean 1-channel communication interface
  - KL6583 EnOcean radio transceiver


## Preperations

- Lees de [documentatie van de EnOcean druktoetsen](https://www.eltako.com/nl/product/professional-smart-home-nl/drukknop-en-schakelaarreeksen-enkele-en-dubbele-wippen-handzenders-en-afstandsbedieningen/f4t65-wg/)

- Lees de [documentatie van de EnOcean temperatuur en luchtvochtigheid sensor](https://www.eltako.com/nl/product/professional-smart-home-nl/drukknop-en-schakelaarreeksen-enkele-en-dubbele-wippen-handzenders-en-afstandsbedieningen/fft65b-wg/)

- Lees de [documentatie van de EnOcean universele dimactor](https://www.eltako.com/nl/product/professional-smart-home-nl/radioactuators-voor-gedecentraliseerde-radio-installatie-in-gebouwen/fud61npn-230v/)

  Raadpleeg de handleiding van de Beckhoff [KL6581 Master and KL6583 Transceiver](https://download.beckhoff.com/download/document/io/bus-terminals/kl6581_kl6583en.pdf). Lees zeker de pagina’s:

  - Product overview => KL6581 - Introduction

  - Product overview => KL6581 - Technical data

  - Mounting and wiring => KL6581 - Contact assignment

  - Mounting and wiring => Cabling between KL6581 and KL6583

  - Programming => Operation with other controllers => Process image

- Lees volgende pagina’s over de EnOcean bibliotheek [TC2_EnOcean](https://infosys.beckhoff.com/english.php?content=../content/1033/tcplclib_tc2_enocean/index.html&id=)

  - Introduction
  - EnOcean
  - M-Bus => Bulletin
  - Programming => POUs => KL6581 (zo goed als ieder item onder KL6581 POUs zal je kunnen gebruiken)
  - Programming => DUTs => KL6581 =>  Structures => KL6581_Input, KL6581_Output, STR_EnOceanSwitch en STR_KL6581
  
  - Programming => Integration into TwinCAT => KL6581 with CX5120 (as example)

## Goals

1.  Leg in je eigen woorden EnOcean uit. Hoe is het opgebouwd en wat kan je ermee?
2.  Beschrijf de aansluitingen van de KL6581.
3.  Beschrijf de ‘FB_KL6581’ functieblok. Welke zijn de in- en uitgangen en waarvoor wordt deze gebruikt?

1.  Beschrijf de ‘KL6581_Input’ structure. Wat is de inhoud en waarvoor wordt deze gebruikt?
2.  Beschrijf de ‘KL6581_Output’ structure. Wat is de inhoud en waarvoor wordt deze gebruikt?
3.  Hoe worden EnOcean toestellen gezocht en ingeleerd (begrippen zoals telegram, [EEP](https://www.enocean-alliance.org/products/eeps/), ORG id.)? Is inleren noodzakelijk?
4.  Beschrijf de aansluitingen en de werking van de EnOcean druktoetsen van Eltako.
5.  Beschrijf de aansluitingen en de werking van de EnOcean temp/hum sensor van Eltako.
6.  Beschrijf de aansluitingen en de werking van de EnOcean dimmer van Eltako.

## Exercises

Programmeer de PLC zodat EnOcean toestellen te besturen zijn en hun data zichtbaar getoond worden vanuit een visualisatie. Voor EnOcean te programmeren dien je de bibliotheek Tc2_EnOcean toe te voegen bij je References.

Programmatie (minimaal vereist om 60% te behalen)

1. Maak gebruik van de ‘FB_KL6581’ functieblok voor de communicatie met de KL6581. Koppel de juiste variabelen met de KL6581. Scan vervolgens alle EnOcean toestellen en toon hun EnOcean IDs in de visualisatie. (10%)
2. Lees de relatieve vochtigheid en de temperatuur in en toon deze samen met hun eenheden in de visualisatie. (15%)
3. Lees de druktoetsen in en stuur één van de aangesloten LED's op de EL2008 terminal aan doormiddel van de FB_Light uit de TC2_BA_Basic library. Gebruik hiervoor de druktoets linksboven als toggle, de druktoets rechtsboven als alles aan en de druktoets rechtsonder als alles uit. (20%)
4. Leer de overige druktoets (linksonder) in op de universele dimmer FUD61NPN en toon aan de docent. (15%)

Bijkomende programmatie (Percentage telt enkel indien minimale programmatie bereikt is).

7.	Toon in de visualisatie de temperatuur waarden van de Eltako FFT65B-wg sensor op een grafiek. (15%)
8.	Stuur een EnOcean telegram in formaat van een druktoets naar de FUD61NPN universele dimactor om deze naar verschillende dimwaarden of een speciale scene 'kinderkamer' te sturen. (25%)

## Questions

For questions and support please place a comment in the pull request titled **Feedback**.

## Remarks

Take care of the setup. Afterwards return the setup to its original state and place it on top of the lab table in the same place. If you notice a defect, you must immediately inform the teacher.
