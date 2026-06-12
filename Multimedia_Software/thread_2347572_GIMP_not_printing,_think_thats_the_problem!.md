---
title: "GIMP not printing, think thats the problem?!?"
date: 2016-12-26
forum: Multimedia Software
---

### Post by mikebellamy2k on 2016-12-26
Hi all, I have a Canon Pixma ip4300 and have no end of trouble. I am using the Gutenprint driver and along with cups it gives some functionality...side note still looking for a working driver fix to allow print quality and ink levels in settings etc...So I've recently updated Ubuntu and lost printing capability with GIMP. Also lost the drivers which worked from a 14.04 fix. So some help with this could stop me getting very annoyed with my own lack of Linux knowledge and the whole system in its entirety...moan over...

FACTS!!!
..Ubuntu 16.10
..Canon Pixma ip4300 USB connected printer.
..Test page comes through and colour set to CMYK.
..Have managed to print a low quality photo, with i think correct colours, with Showfoto.
..Annoyingly works fine with Windows!!
..GIMP sends to the printer and it logs a job in the printer settings.
..STOPS there and just says processing!!
..Can't find drivers other than Gutenbloodyprint.

 Help please its driving me insane!!!!

:confused::confused::confused::confused::confused::confused::confused:

---

### Post by Autodave on 2016-12-27
I have had very limited luck w/Canon printers in Linux. Did you go to Canon's website and search for drivers?

---

### Post by mikebellamy2k on 2016-12-27
Seems to be no decent drivers any where for Canon. Especially for more up to date versions of Ubuntu. I don't really know why it's such an issue and Windows have pretty much got it sorted.

---

### Post by Autodave on 2016-12-27
It is not the fact that Windows has it figured out. What is a fact is that Canon doesn't feel that there enough Linux user's out there for it to be worth their time to write a linux driver.  Go to Canon's website and leave an email telling them about your displeasure.

---

### Post by mikebellamy2k on 2016-12-27
Yes I may. It doesn't really help my situation though as any time from now onwards any printer including the one I have may or may not work with Ubuntu. What's the point in having the OS if you can't do a basic function by today's standard like easily connect and use a printer. That was the reason for my post and to see whether anyone else had a solution to GIMP issues which have started since the Ubuntu 16.10 update. There is a new stable release soon I hope, GIMP 2.10 possibly, will have to see if that works better. Drivers will just have to remain an issue unless someone codes a solution. Turning back to windows everytime I need to print a photo leaves a bad taste in my mouth.

---

### Post by mikebellamy2k on 2016-12-28
Possible solution found and I hope it is the final one!!!!

[https://ubuntuforums.org/showthread.php?t=2347310](https://ubuntuforums.org/showthread.php?t=2347310)

---

### Post by Autodave on 2016-12-28
I hope that link you found helps you out. I learned a long time ago to make HP my printer of choice. I have never had to do anything w/an HP printer other than hook it up and turn it on and Linux finds it right away and it just works.

---

### Post by SeijiSensei on 2016-12-28
The [Gutenprint](http://gimp-print.sourceforge.net/index.php) project has an experimental driver for your printer.  I've never installed one from there, but it is supposed to be compatible with CUPS.

---

### Post by mikebellamy2k on 2017-01-05
Ok thanks [SIZE=2][FONT=arial][[COLOR=#000000]SeijiSensei[/COLOR]]("https://ubuntuforums.org/member.php?u=698195")[/FONT][/SIZE][COLOR=#000000] . I have managed to install the pre4 Gutenprint from the link in the last post. 
As with the last driver (CUPS+Gutenprint v5.2.11) the new driver (CUPS+Gutenprint v5.2.12-pre4) automatically recognises the canon printer. If set to CMYK colour a successful test page is printed. However once in GIMP the data is sent to the printer and then fails from there. It had a 'filter failed' error in the printer manager app. Once cancelled it printed fine from GIMP set up with the Turboprint driver.
Have found the same document prints with Libreoffice as well with the Gutenptrint drivers. 
I have attached some screenshots of the attributes once failed to print with Gimp and Gutenprint.
[/COLOR][ATTACH=CONFIG]273063[/ATTACH][ATTACH=CONFIG]273064[/ATTACH][ATTACH=CONFIG]273065[/ATTACH]

So where to go from here???

---

### Post by Autodave on 2017-01-05
Just to reinforce what I said earlier, my HP Laserjet 277dw arrived today. I plugged the USB cable from my wife's machine and it was recognized and worked instantly. Then, from this machine, I had wireless printing in about 30 seconds.

I know this doesn't help you at all and I am hoping that you find the driver(s) that you need, but for anyone coming new to Ubuntu or thinking of getting/replacing a printer, HP is the easy route to take.

---

### Post by mikebellamy2k on 2017-01-05
NO that doesn't help!!!!!!!

Only kidding thanks for the heads up. I will find a fix for this!! :popcorn:

---

### Post by SeijiSensei on 2017-01-05
GIMP natively uses RGB rather than CMYK.  See this for how to convert the color scheme: [http://askubuntu.com/questions/114858/how-to-convert-image-to-cmyk-in-gimp](http://askubuntu.com/questions/114858/how-to-convert-image-to-cmyk-in-gimp)

---

### Post by mikebellamy2k on 2017-01-05
I'm not sure that's the problem. Gimp is not printing at all with Gutenprint although the test page comes out OK when set to CMYK. Also it has limited settings such as only 600*600 resolution.

---

