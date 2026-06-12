---
title: "lg dare (mp3/phone tools and linux)"
date: 2008-07-19
forum: Multimedia Software
---

### Post by sonaural on 2008-07-19
does anyone know the program to transfer music from a ubuntu system to the new lg dare cellphone?

---

### Post by rushikesh988 on 2008-07-19
why don't you try GAMMU or WAMMU for file transfer and As per I know I Think that if you swicth off your cell phone and connect it to your PC then It will connect itself as a USB DEVICE(PEN DRIVE)

---

### Post by sonaural on 2008-07-21
installed gammu and gmobilemedia but can't figure out how to use gmob and gammu doesn't show up on the system

i opened gmob but don't know how to configure.  i connected my phone (an lg dare) but can't get the system to acknowledge it even though i restarted both the phone and the computer

---

### Post by NilsE on 2008-07-21
Have you tried Bitpim.  I am not sure if the version in the repositories supports the Dare since it is new but you can go to their web site and check for a newer version with Dare support.

[http://www.bitpim.org/](http://www.bitpim.org/)

---

### Post by zstraub1 on 2008-11-06
holy god please reply if the last suggestion worked

---

### Post by JesterDev on 2008-11-08
Bitpim works. I use it all the time with my LG Dare. However I use it under windows (the only reason I run windows...) because I cannot find a 64-bit version. 

I attempted an install via DEB package, so maybe I'll try source here in a bit.

But yeah, it works. Great for ringtones, flash games, moving pictures from phone to PC, and so on.

Edit: I tried 1.0.6, and apparently there is 1.0.5, that can be had through synaptic, haven't tried that one yet, (installing now) but will post back when I do.

---

### Post by JesterDev on 2008-11-08
1.0.5 does not work with my phone (VX 9700) but many other earlier versions are supported so you may have better luck. :) If you find a 64-bit version of 1.0.6 please let me know!

---

### Post by zstraub1 on 2008-11-24
Jester,

I got Bitpim 1.0.6. I got Bitpim to recognize my phone (LG DARE Vx9700). Now I want to throw a playlist on the phone but Bitpim is having errors doing so. Apparently the format it uses is WPL, so I converted the playlist from M3U to WPL, and it still didn't work.
Should I try getting Bitpim for windows, and run it on that side of my harddrive?
Basically what am I missing here?

---

### Post by sceo on 2009-01-23
zstraub1 - how did you get BitPim 1.0.6 to recognize your Dare?  It can't find mine.  I am connecting with USB, and I'm choosing "Data" when the phone asks me how to connect.  I tried "auto" port and the "USB modem" port.

---

### Post by asparatu on 2009-01-29
I would like to know how you go to work in ubuntu too. I have been tring to get to work. Im using the BitPim 1.0.7.20081215 - Test and doesnt work..
shane

---

### Post by pwc on 2009-02-11
Transfering music from your computer to the LG Dare is quite simple. Connect with the USB cable. Then on your dare, go to Settings & Tools-> Tools-> USB Mass Storage. A window on your computer screen will open, this window shows the folders in the added card memory(you must have added card memory, THIS WILL NOT WORK WITH JUST INTERNAL MEMORY!) Then just copy from your computer into the music folder.

---

### Post by DAMurphy on 2009-02-27
Oh, yeah just figured this out.  Wouldn't connect to phone unless I ran BitPIM as super user...  connects now.  Haven't messed around with it yet.

---

### Post by Jesta384 on 2009-04-09
anyone have any tools for 64 bit ubuntu 9.04?

---

### Post by mjbauer95 on 2009-07-26
> **Jesta384 said:**
> anyone have any tools for 64 bit ubuntu 9.04?

Run:
```
svn co https://bitpim.svn.sourceforge.net/svnroot/bitpim/trunk/bitpim
python src/bp.py

```

---

### Post by spanky1023 on 2009-10-04
> **pwc said:**
> Transfering music from your computer to the LG Dare is quite simple. Connect with the USB cable. Then on your dare, go to Settings & Tools-> Tools-> USB Mass Storage. A window on your computer screen will open, this window shows the folders in the added card memory(you must have added card memory, THIS WILL NOT WORK WITH JUST INTERNAL MEMORY!) Then just copy from your computer into the music folder.

yes that works, BUT when i try to listen to the songs on the phone it doesnt seem to find anything that i just uploaded to the phone. it shows it on my laptop that the info is on the card in my phone, but my phone doesnt find it.

any ideas?

---

### Post by ponderworks on 2009-11-12
Got my VX9100 ENV working using information and file at

[http://ubuntuforums.org/showpost.php?p=1317977&postcount=24]("http://ubuntuforums.org/showpost.php?p=1317977&postcount=24")

and the advice given here to startup BitPim using **sudo**.

---

### Post by EricMattessich on 2009-12-19
so i just ran across this thread and if you guys are still having trouble on 64bit bitpim access to your dare just try ```
gksudo bitpim
``` in terminal, then go to settings and set the phone as dare and everything should work great.

---

