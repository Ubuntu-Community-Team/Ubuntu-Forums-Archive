---
title: "Artec T1 again... but it works on sidux, whats the difference?"
date: 2007-02-27
forum: Multimedia &amp; Video
---

### Post by mmoalem on 2007-02-27
hi there all - i have the artec t1 usb dvb card that give som much grief to so many linux users. i have tried to get it working on various distros for the last year or so and never got anywhere (so had to keep a windows machine going just for recording dvb programs) - that said yesterday i booted sidux livecd and it found the card and scanned for channels straight out-of-the-box! 
now sidux is basically debian so i thought there might be a way of copying/replacing some files from sidux into my edgy installation to make it work... i wouldnt have a clue how to start but if anyone can advise on it i would appriciate it
cheers
michel

---

### Post by mmoalem on 2007-03-04
can report some success!
installed ubuntu feisty herd 5 (alpha) hoping the newer kernel will work
updated and upgraded through apt
followed the installation on:
[http://www.ubuntuforums.org/showthread.php?t=198423](http://www.ubuntuforums.org/showthread.php?t=198423)
replacing the nebula firmware with the an2235 one and answering accordingly after make config ('m' to the dibcom ones) and rebooted
plugged in the artec t1 and it lighted up green and lsusb recognised it as dibcom dvb device and so is dmesg
now i have to figure out what software i can use to scan and record... and than hope it will work on feisty alpha...
but this is the furthest i ever got with this card and i'm happy

---

### Post by BobbyBionic on 2007-04-22
Hello

In theory with the new kernel v4l is inside, I don't understand.

So, I try to do what you say (2.6.20-15-generic) and I always have this error :
*** Error during writing of the kernel configuration.

make[1]: *** [config] Erreur 1
make[1]: quittant le répertoire « /home/guillaume/v4l-dvb/v4l »
make: *** [config] Erreur 2
Very strange, there is any other error instead of this.

I don't understand, perhaps it's the 2.6.20-15 which is faulty ? Or the v4l sources ?

Without doing nothing, a few days ago, the box light on, since I want to understand (I do another install af feisty, doing the same, but no results, it was a miracle...).

Any idea ?

Thanks :)

---

