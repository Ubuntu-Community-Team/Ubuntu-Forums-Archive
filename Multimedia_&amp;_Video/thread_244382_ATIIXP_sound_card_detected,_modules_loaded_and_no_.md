---
title: "ATIIXP sound card detected, modules loaded and no sound"
date: 2006-08-26
forum: Multimedia &amp; Video
---

### Post by tommaddox on 2006-08-26
Hi everybody!

I hava a laptop ASUS A6R, with chipset ATI radeon xpress 200M (graphics embedded in chipset). The soundcard is ATIIXP, also embedded in the chipset, and some additional sound chipset from Analog Devices is added to this (for winXP I have some additional drivers for it). Alsa-mixer reports a card ATIIXP, chipset by analog devices. Also the snd-atiixp modules are loaded. I have read the comprehensive sound gide, but according to it everything should be allright. I played with the settings of alsa-mixer, with no result. 

Now my question is, does anoyne have a similar hardware, and are you able to make it working ?

Thanks in advance.

---

### Post by encompass on 2006-08-26
I use the driver... I have a shuttleX zen with an ati9100IGP similar to yours and the same sound card.  I found no issues with it.  You may want to check your settings if you have external amp on or off.  You could also see if all sounds are at full.  Then see what happens.
Are you tring to play the sound threw an amped or external speakers?  Try just the ones built into the laptop.
Hope this helps... I will look up your laptop in google too.

---

### Post by encompass on 2006-08-26
OH dear...
[http://www.marcussmit.nl/linux-on-laptops/asus_a6r_fc5.html](http://www.marcussmit.nl/linux-on-laptops/asus_a6r_fc5.html)
Still looking though...

---

### Post by encompass on 2006-08-26
OH DEAR?
[http://www.ubuntuforums.org/showthread.php?t=235115&page=2](http://www.ubuntuforums.org/showthread.php?t=235115&page=2)

---

### Post by tommaddox on 2006-08-26
Well. I have tried all settings in alsa-mixer. But what may be a solution, is loading some driver from a compatibile card (ati claims that this soundcard is compatibile with sounblaster pro). 
But I do not know how to do it. Load module from soundblaster pro, but how to say to alsa that the card is not atiixp but but soundblaster pro? Is there any hardware configuration file for alsa ?

---

### Post by encompass on 2006-08-26
[http://www.beginningubuntu.com/dapper_tips.html#Sound_on_my_weird_notebook](http://www.beginningubuntu.com/dapper_tips.html#Sound_on_my_weird_notebook)
you tried this?  He sounds pretty confident that it works.
What are you using to play the sounds for tests.
```
speaker-test -c 2 -t wav
```
should get you a nice long sound that constantly goes so you can listen as you fiddle  just run it in the terminal and press cntrl c to quit it.

---

### Post by tommaddox on 2006-08-26
Tanks a lot ! 
The link to
[http://www.beginningubuntu.com/dappe...weird_notebook](http://www.beginningubuntu.com/dappe...weird_notebook)
helped me a lot. Indeed my problems were caused by the mixer settings, namely the Master Surronud. Thanks a lot. I hope that this thread will be helpful for other people googling for finding solution to their "no sound" problem with ATIIXP in A6R notebook.
And once again thanks.

---

### Post by encompass on 2006-08-27
Feels good to know I helped.  Your welcome.

---

