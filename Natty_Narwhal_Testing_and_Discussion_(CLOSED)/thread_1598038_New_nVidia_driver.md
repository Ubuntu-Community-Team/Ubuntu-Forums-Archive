---
title: "New nVidia driver"
date: 2010-10-16
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by plun on 2010-10-16
EDIT latest
[http://www.nvnews.net/vbulletin/showthread.php?p=2345016](http://www.nvnews.net/vbulletin/showthread.php?p=2345016)



----------------------------------------------


Ver 260.19.12 is out

Info:
[http://www.nvnews.net/vbulletin/showthread.php?t=122606](http://www.nvnews.net/vbulletin/showthread.php?t=122606)

Ubuntu X-swat ppa:
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

Natty users must for the moment use maverick as repo adress


Gtkperf  (GT330M)

```
GtkCheckButton - time:  0.10
GtkRadioButton - time:  0.17
GtkTextView - Add text - time:  0.56
GtkTextView - Scroll - time:  0.19
GtkDrawingArea - Lines - time:  0.39
GtkDrawingArea - Circles - time:  0.45
GtkDrawingArea - Text - time:  0.37
GtkDrawingArea - Pixbufs - time:  0.14
 --- 
Total time:  5.65

```

---

### Post by MishaAct on 2010-10-16
Performance was noticeably improved for me: from &#8776; 3.8&#8212;4.0 seconds down to 3.1-3.3

---

### Post by laithbsoul on 2010-10-16
Does anyone know if this fixes the problems with maverick and the drivers bugging with the pulse audio? I had so many problems with the drivers in the repo and the ones on nvidia's website screwing up pulse audio in one way or another. I still have no clue why though.

---

### Post by taavikko on 2010-10-16
The nvidia-current from x-swat (260.19.12)
freezes the X on boot, like the one that maverick shipped by default (260.19.06)

GT 330m on sony vaio F series laptop.

Luckily the 256.* eries driver work and I can use this junk...

---

### Post by plun on 2010-10-16
> **taavikko said:**
> T
GT 330m on sony vaio F series laptop.



Yep... Sony Vaio is junk....):P

330M on a Samsung R580 works excellent...

Pure Intel+nVidia combination....:popcorn:

---

### Post by autocrosser on 2010-10-16
The xswat driver works great here---SLI-dual 9800GT cards--Gigabyte EX58-UD4P i7 system.....

---

### Post by taavikko on 2010-10-16
> **plun said:**
> Yep... Sony Vaio is junk....):P


:lolflag:

I just bought it because of i7-720 and FullHD display...
Whole lotta money for a piece of ****

---

### Post by plun on 2010-10-16
> **taavikko said:**
> 
I just bought it because of i7-720 and FullHD display...
Whole lotta money for a piece of ****

Well....I don't know what Sony put inside this beast but I have helped other users with this page within my country

[http://code.google.com/p/vaio-f11-linux/wiki/NVIDIASetup](http://code.google.com/p/vaio-f11-linux/wiki/NVIDIASetup)

First it was the kernel and now it seems to be the driver....

Made in Sony....

---

### Post by taavikko on 2010-10-16
> **plun said:**
> Well....I don't know what Sony put inside this beast but I have helped other users with this page within my country

[http://code.google.com/p/vaio-f11-linux/wiki/NVIDIASetup](http://code.google.com/p/vaio-f11-linux/wiki/NVIDIASetup)


CustomEdid was the first thing to apply when this laptop was purchased and windows erased to give room for ubuntu+1 ;)

Just to mention, I did install the OEM windows7 that came with this piece of **** and the GPU didn't work with windows drivers either... It's nice to use laptop with 800*600 resolution when it's capable of 1920*1080

Anyone suffering from freeze on boot:
[http://www.nvnews.net/vbulletin/showthread.php?t=155218](http://www.nvnews.net/vbulletin/showthread.php?t=155218)

---

### Post by exploder on 2010-10-17
The new driver seems to be an improvement with my GT 220, the temperature is lower and things are more responsive.

---

### Post by plun on 2010-11-10
New pre-release driver, version 260.19.21

[http://www.nvnews.net/vbulletin/showthread.php?p=2345016](http://www.nvnews.net/vbulletin/showthread.php?p=2345016)

Works just fine including Compiz 0.9.2.

X-swat ppa:
Not build yet

---

### Post by Quackers on 2010-11-11
> **plun said:**
> Well....I don't know what Sony put inside this beast but I have helped other users with this page within my country

[http://code.google.com/p/vaio-f11-linux/wiki/NVIDIASetup](http://code.google.com/p/vaio-f11-linux/wiki/NVIDIASetup)

First it was the kernel and now it seems to be the driver....

Made in Sony....

The Sony Notebook Control pos has a lot to answer for!

---

### Post by plun on 2010-12-03
Since yesterday we have a new driver, ver 260.19.26 but this one is rather strange... just presented in an thread in the nVidia forum...

[http://www.nvnews.net/vbulletin/showthread.php?t=157563](http://www.nvnews.net/vbulletin/showthread.php?t=157563)

X-swat is serving this one...

I have never run a Ubuntu version better then this....;)

---

### Post by emas80 on 2010-12-08
Hi, installed last week this new driver, but after first reboot (I reboot once a week, my nb is always on or suspend-to-ram) suspend-to-ram doesn't work anymore...

My note freezes just when suspending (black screen, nothing happens, fans still working, nothing in the log files), or when waking up (black screen, fan working, nothing else).

I use it with last 2.6.36 vanilla kernel, before the nvidia upgrade all was working fine, has anybody else seen some problems?

No kernel changes were made, I don't remember what Ubuntu-upgrades run last week, as far as I remember the only "sensible" upgrade was Nvidia drivers.

---

### Post by cariboo on 2010-12-08
Most of us here are running the  2.6.37-8-generic #21 kernel, what version are you using?

---

### Post by seenthelite on 2010-12-09
Kernel 2.6.37-8 generic and 260.19.26 working OK.:D

---

