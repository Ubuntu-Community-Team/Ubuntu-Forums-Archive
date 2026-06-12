---
title: "capture/ tuner cards"
date: 2010-12-19
forum: Mythbuntu
---

### Post by oldsoundguy on 2010-12-19
Have found several lists for capture/tuner cards but a bit confusing to someone new to Myth.

I have in possession one of the listed "good" cards .. a DiVico Fusion HDTV 5 RT Gold.

My proposed source will be digital cable (Comcast).
Will this capture/tuner work? or do I have to go shopping? and what am I to look for if I do?

---

### Post by thatguruguy on 2010-12-19
My suggestion is just try it and see. If it's already installed in a box using ubuntu, you can use tvtime to watch whichever analog signals are being carried by your carrier, and metv to scan for and watch any unencrytped digital signals.  For instance, I have Insight cable which carries both analog and digitial. Although not all of the analog channels have unencrypted digital counterparts, many of them do (e.g., all of my local channels, plus syfy, cartoon network and AMC, among others).

---

### Post by oldsoundguy on 2010-12-19
I have had to install d/a converters/tuners furnished by Comcast in order to run the two analog sets I have in my home. It is my assumption that the entire cable is digital .. and HDTV is encrypted for sure as have to use a HDTV/digital tuner to run the big screen

---

### Post by newlinux on 2010-12-19
In most places local HD stations (major networks) are unencrypted via QAM. depending on where you live you could also use the dvico for OTA ATSC capture, which could give you the locals in HD too. You could put your zip into [http://www.silicondust.com/support/channels/](http://www.silicondust.com/support/channels/) and see what others have reported...

---

### Post by oldsoundguy on 2010-12-19
> **newlinux said:**
> In most places local HD stations (major networks) are unencrypted via QAM. depending on where you live you could also use the dvico for OTA ATSC capture, which could give you the locals in HD too. You could put your zip into [http://www.silicondust.com/support/channels/](http://www.silicondust.com/support/channels/) and see what others have reported...

link is OK .. the search on the page is not OK! Gives a totally unreadable page for a few seconds and then goes blank!!

Once again .. the language of video world, while it is universal, needs some clarification and definition for a Myth noob.  Especially what all the abbreviations mean and what it does.

---

### Post by thatguruguy on 2010-12-19
Mythtv can't decode encrypted channels. Your choice of tuner is irrelevant as far as encryption goes. Which channels are encrypted and which ones are not encrypted are up to your cable provider.  However, cable providers in the US are required to carry your local channels in an unencrypted digital format.

---

### Post by oldsoundguy on 2010-12-19
parts are due to land next week .. will give it a shot and get back with some results by next weekend.  Thanks for the information.  I DO know that I will be asking more questions in the future.

As usual, the Ubuntu forums come through!

---

### Post by newlinux on 2010-12-19
> **oldsoundguy said:**
> link is OK .. the search on the page is not OK! Gives a totally unreadable page for a few seconds and then goes blank!!

Once again .. the language of video world, while it is universal, needs some clarification and definition for a Myth noob.  Especially what all the abbreviations mean and what it does.

Google and wikipedia are your friends

QAM - [http://en.wikipedia.org/wiki/QAM_%28television%29](http://en.wikipedia.org/wiki/QAM_%28television%29)

ATSC - [http://en.wikipedia.org/wiki/ATSC_tuner](http://en.wikipedia.org/wiki/ATSC_tuner)

Your dvico can tune unencrypted QAM (digital cable), ATSC (Over the Air digital broadcast direct from your local stations) and NTSC (analog). (I have a fusion 5 lite, different chipset but same capabilities).

---

### Post by nickrout on 2010-12-19
> **oldsoundguy said:**
> I have had to install d/a converters/tuners furnished by Comcast in order to run the two analog sets I have in my home. It is my assumption that the entire cable is digital .. and HDTV is encrypted for sure as have to use a HDTV/digital tuner to run the big screen

Anything that is encrypted needs to go through the provider's set top box and then be captured by an analogue capture device. You can capture at SD resolution by any number of tuner cards. If you want to capture at HD resolution the only real option is the HDPVR which requires component video input.

---

### Post by efball3 on 2010-12-20
I have the dvico fusionhdtv7 dual express and Comcast cable.  I get HD channels for ABC, CBS, NBC, Fox, PBS.  I should get CW and a couple others (I do with Windows Media Center, but can't find them in MythTV).

---

