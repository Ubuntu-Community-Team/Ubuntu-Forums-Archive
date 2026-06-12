---
title: "DVB-T and Aussie Channels, not all pick up"
date: 2007-04-21
forum: Multimedia &amp; Video
---

### Post by MistaED on 2007-04-21
Hey all, I have a DVB-T HDTV tuner card which uses dvb-bt8xx. It works fine with kaffeine, however when I scan for channels I have to set a preset transponder file like "au_north_shore" to get only sydney channels. 

On every other TV tuner software in windows or even stand alone set top boxes, they scan for all possible channels out there and are not narrowed down to just these presets. If anyone is familiar with the South-West Sydney area, we are able to get both Sydney and Wollongong channels with the right antennas, however with these presets I cannot get Wollongong channels and only recently these files have been updated to contain the "D44" channels from Sydney in the latest feisty fawn.

So why is this only limited to linux's implementation of DVB/xine/whatever? It doesn't make sense to me.

Cheers all
-MistaED

---

### Post by Erlander on 2007-04-22
I've just looked at the DVB Settings in Kaffeine.

I don't know your location but I think there may be a problem with Kaffeine.

I normally use Au-Melbourne for a scan.  I just tried Au-Unknown thinking it might be the answer to your problem.  But it only scanned the ABC Channels and not any of the other.

Mythtv is much easier to setup under Feisty.  Maybe its the answer for you.

I'll have a look at the scanning options in it and get back.

Rob

---

### Post by Erlander on 2007-04-22
Just looked at my Mythtv setup

The settings for scanning are just Australia.  No local settings so maybe it would work for you.

Rob

---

### Post by angelman99 on 2007-04-23
I found the au-location files (hint they are set as hidden).
I've started hand crafting one for the Rockhampton district (Mt Hopeful transmitter).
Only got 2 channels so far, SBS and Ten.
Got the frequencies for the others but none of the other information. The "official" site is next to useless [http://www.dba.org.au/index.asp?sectionID=22](http://www.dba.org.au/index.asp?sectionID=22)
I have logged a request for info with them, so I should bag them out to much, because they may yet surprise me and respond quickly to my e-mail request :-)
the website assumes you are just plugging in a set top box. I can understand giving the basic information "most" users need, but they should have an advanced or technical info button as well.

---

### Post by MistaED on 2007-04-25
Cheers all, I looked at the text files directly and I managed to put one in for ABC Illawarra so now I can watch the chaser tonight with a clear picture ;) still odd how linux dvb requires premade transponder details when set top boxes somehow just pick them up automagically. Maybe I'm missing something here, who knows.

Speaking of MythTV, would that work well with running it entirely from a window manager? Somewhat like how winders media center opens up from a vista desktop. Last time I tried to get mythtv to do anything I was extremely confused with it and it wanted to take over all of xorg so I gave up.

-MistaED

---

### Post by Gruelius on 2007-06-15
Ive had a look at the au_melb file and i have no idea on how i should transpose the info. Cant i just get it to look at all towers somehow?

Anyway here are the freq's i want

ABC Network On-Air  	UHF 47 Hor  	662.5 MHz  	Bruce Crescent FERNTREE GULLY
Seven Network 	On-Air 	UHF 41 Hor 	620.5 MHz 	Bruce Crescent FERNTREE GULLY
Nine Network 	On-Air 	UHF 44 Hor 	641.5 MHz 	Bruce Crescent FERNTREE GULLY
Network Ten 	On-Air 	UHF 54 Hor 	711.5 MHz 	Bruce Crescent FERNTREE GULLY
SBS Television 	On-Air 	UHF 50 Hor 	683.5 MHz 	Bruce Crescent FERNTREE GULLY

Cheers

---

### Post by Gruelius on 2007-06-16
I managed to get a good tune. This is how i did it.

From the linux TV wiki i did the following:
```
mkdir ~/.tzap
scan /usr/share/doc/dvb-utils/examples/scan/dvb-t/au-Melbourne > /.tzap/channels.conf
```

Then i put the file onto this page to convert it into a channels.dvb file for kaffeine [http://lab.infodatei.de/conf2dvb/](http://lab.infodatei.de/conf2dvb/) . 

One problem is that ABC HD, 7 HD and 9 HD all have no sound. running tzap -s doesnt work because it isnt listed as a paramater! If someone can give me a hand that would be great.

---

### Post by Erlander on 2007-06-16
The HD channels have AC3 sound so you almost certainly need to install a codec to deal with this.

If you can't find the right one I'll check and see what I have installed.

Rob

---

