---
title: "radeon hd 4870 x2 sli + 11.04 Natty going black"
date: 2011-04-15
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Beaverfook on 2011-04-15
Hi ubuntuforums! 
I got me one hell of a supercomputer for all my video-rendering needs. I tried installing ubuntu but didnt make it past the loading screen. 
the problem is my two sli radeon hd 4870 x2 and 11.04 Natty. 
Yesturday i saw the mouse for a sec, OMG! 
Anyways, mostly, i only get a black screen and a totally freezed out computer. ctrl+alt+f1 dont do nothing. 
First time tough, i got a Failed to bind error screen that didnt make any sense. 
Tried 10.04 lts, but there he couldent discover my disc, altough i run it as achi. 
Any ideas?

---

### Post by s.fox on 2011-04-15
Thread moved to [Natty Narwhal Testing and Discussion]("http://ubuntuforums.org/forumdisplay.php?f=394")

---

### Post by Harry33 on 2011-04-15
You have quite a high-end ATI GPU there.
May very well be that the open source driver (xserver-xorg-video-ati) does not fully support it yet.
Also if the latest fglrx doesn't not work, there is even less we can do; a proprieatary driver you see.

---

### Post by tormod on 2011-04-15
The card should be supported by the default driver, but there might be some issues with running 2 cards at the same time. I believe in any case only one of the GPU-cores per card will be enabled.

fglrx should support multiple cards or cores: [http://www.phoronix.com/scan.php?page=article&item=amd_4870x2_open](http://www.phoronix.com/scan.php?page=article&item=amd_4870x2_open)

There are some issues with HD3870X2 reported in [http://pad.lv/755715](http://pad.lv/755715) where also the "fail to bind" messages appear but I think it is a more general R600 issue. I do not know if the dual-GPU (X2) properties cause some common issues here.

---

### Post by Beaverfook on 2011-04-15
So, tried to disconnect one of the cards, didnt help. Seems like its the dual gpus messing around. 
I miss the boot in safe grapical mode option :( 
Im booting up with dual cards to see if can get back to the failed to bind screen again. 
Btw, on Backtrack 4, the fix-vesa command manage to get my screen working with startx. Can i modify installation images to execute that command?

---

### Post by cubeist on 2011-04-15
Hi,
Your card is an R700 series, and according to this chart, you should have very decent support with opensource drivers.
[http://www.x.org/wiki/RadeonFeature](http://www.x.org/wiki/RadeonFeature)

Try this. At Grub, boot into recovery mode. Once in a recovery terminal, do this:
```
sudo apt-get purge fglrx
```
```
sudo apt-get install xserver-xorg-video-ati
```

then, since your card uses KMS, lets make sure you don't have an xorg file
```
mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak 
```
reboot!

You will have to execute these commands as sudo

---

### Post by tormod on 2011-04-15
cubeist, he is talking about booting the installation media, so he has probably not installed any fglrx drivers.

Beaverfook, you can boot with the "nomodeset" kernel option to see if X runs better without KMS. I am not sure if the "xforcevesa" option still works. Otherwise, boot with the "text" option, make an /etc/X11/xorg.conf like this:
```
Section "Device"
 Identifier "mycard"
 Driver "vesa"
EndSection
```
and start X with "sudo start gdm".

---

### Post by Beaverfook on 2011-04-22
Finally home from easter vacation! :) 
If i spam ctrl+alt+f1 while booting and wait for it to load in there and then, after some thinkin ctrl+alt+f7 to the desktop it works like a charm... Trying to install now, i'll be back with a log soon ;)

oh, btw, the xorg-config did the trick i figured.

---

