---
title: "Dvd Player - Breezy"
date: 2005-10-20
forum: Multimedia &amp; Video
---

### Post by dayal_78 on 2005-10-20
Hi,
I have breezy badger installed on my Dell Inspiron 6000.
When I insert a DVD the totem dvd player starts automatically but it just errs out saying "Couldn't get title information....". 
I am wondering is totem usable?? If not whats the best dvd player for breezy?
thanks
Dayal

---

### Post by yage on 2005-10-21
It seems you are missing libdvdcss
```
sudo apt-get install libdvdcss2
```
Hope this helps you!

---

### Post by dayal_78 on 2005-10-21
[QUOTE=yage]It seems you are missing libdvdcss
```
sudo apt-get install libdvdcss2
```
Hope this helps you![/QUOTE]
Hi,
thanks for the input.
I installed libdvdcss2 but now when I try to play the dvd with totem it says 'playing' and just hangs. Am I missing something?

Thanks
Dayal

---

### Post by crudh on 2005-10-21
Hi

I tried installing libdvdcss2 but I can't find it. I have the official, universe, multiverse and non-free repositories configured. Is there any other repository I need?

---

### Post by dayal_78 on 2005-10-21
Add this to your sources.list:

deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

---

### Post by crudh on 2005-10-21
Thanks!

---

### Post by larry98765 on 2005-10-22
Hi all,

I've been getting the following error when trying to play a DVD:

```
Error invoking "dvdnav_get_next_block": Error reading from DVD..
```

Might the solution above also be a fix for this?

Thank you

---

### Post by Vlammetje on 2005-10-23
same fix... installing libdvdcss solved that for me ;)

---

### Post by TrumpetMan258 on 2005-10-24
What about that hanging problem that dayal_78 mentioned?  I'm having the same problem after installing libdvdcss2.  Any fix for it?

---

### Post by YR600 on 2005-10-24
Hi,

I have libdvdcss2 already installed and it still says could not play dvd, could not read title information?

what else should I do?

---

### Post by Svictor on 2005-10-24
Once you have installed libdvdcss2, you could try other players than totem. I use either xine-ui, or ogle. Mplayer would also work (but the repository version won't read dvds on my computer, so I recompiled it from source). Ogle has been designed from start to be a dvd player, so it has support for dvd menus. Mplayer doesn't (as far as I could see) and xine does somehow ... I would suggest ogle for a try. It's in the repos, you can install it through synaptic.

---

### Post by pjs_flyer on 2005-10-26
I had the same problem with Totem, even after installing libdvdcss2 (which I got from tamir - [http://tamir.nooms.de/wiki/)](http://tamir.nooms.de/wiki/)), but can confirm that Ogle works a treat once that package is installed.  However, even Ogle is jumpy until you enable DMA (see this "howto" - [http://ubuntuguide.org/#speedupcddvdrom](http://ubuntuguide.org/#speedupcddvdrom))

P.

EDIT: btw, I needed to change the ref in the howto from "cdrom" to "hdc", as advised elsewhere on this most excellent forum

---

### Post by pjs_flyer on 2005-10-28
...and although totem-gstreamer still didn't work, changing to totem-xine did!

---

### Post by Luke Psywalker on 2005-10-28
I get better peformance out of gxine (xine-ui with gtk look) than totem-xine in terms of vertical refresh, so it is my current recomendation as a dvd player for breezy.

---

### Post by jaggedpulse on 2005-10-29
I can't connect to the internet with my Breezy yet and I was wondering if I could download this package in Windows XP, put it on CD, and then put it onto my computer with Ubuntu on it. I don't seem to have the package anywhere...

---

