---
title: "My cd drive is running too fast"
date: 2008-05-03
forum: Multimedia Software
---

### Post by Sathors on 2008-05-03
So I've installed Ubuntu (Gutsy Gibbon) a few weeks ago, and when I want to listen music from a cd, my cd driive begins to run too fast and this during all the listening. It works perfectly on Windows so I was guessing if it were the music players I use (Amarok and CD juicer).


I am very grateful for your answers ^^

PS : excuse me for typing mistakes but I'm french.

---

### Post by Sathors on 2008-05-04
Anybody can help me ?

---

### Post by NightwishFan on 2008-05-04
Running too fast? Not sure exactly what you mean. Odd, though as mine is a newer lightscibe and it all works fine.

---

### Post by presston on 2008-05-04
1) mount -o speed=<speed>
2) hdparm -E <speed>
3) eject -x <speed>
4) cdspeed

---

### Post by presston on 2008-05-04
[http://www.linuxfocus.org/~guido/cdspeed-0.4.tar.gz](http://www.linuxfocus.org/~guido/cdspeed-0.4.tar.gz)   for download

description

> Modern cdrom drives are too fast. It can take several seconds on a 60x speed cdrom drive to spin it up and read data from the drive. The result is that these drives are just a lot slower than a 8x or 24x drive. This is especially true if you are only occasionally (e.g every 5 seconds) reading a small file. This utility limits the speed, makes the drive less noisy and the access time faster. cdspeed is also very good if you prefer to listen to the musik on your mp3 CDs rather then the noise of your CD drive.

Note: recent versions of the eject command include the functionallity of cdspeed (via the -x option).

taken from: [http://www.linuxfocus.org/~guido/#cdspeed](http://www.linuxfocus.org/~guido/#cdspeed)

---

### Post by Sathors on 2008-05-04
When I say it runs too fast, I mean that the cd drive keeps humming very loudly while reading the data, and this during all the track.

I'll try the solution you advise, hoping it will solve my problem, but first I have to find once more how to unpack and install a .gz from the shell :lolflag:

I'll keep you informed, thanks

---

### Post by NightwishFan on 2008-05-04
Oh ok I get it now.

---

