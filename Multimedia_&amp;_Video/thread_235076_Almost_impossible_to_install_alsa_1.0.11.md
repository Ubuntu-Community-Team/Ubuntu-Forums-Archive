---
title: "Almost impossible to install alsa 1.0.11"
date: 2006-08-12
forum: Multimedia &amp; Video
---

### Post by chiron69 on 2006-08-12
Good morning

I've spent already some hours on this and I still don't have any solution.

I have an Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03) with Ubuntu 6.06

There is no sound from Mic or Line, but when I unplug the microphone from the plug I hear some ticks.

The microphone is OK on this system with windows XP
The microphone is ok with another system either with ubuntu or windows XP.
Adjusting with alsamixer NOK.

So I have searched and found this thread:
[http://www.ubuntuforums.org/showthread.php?t=187156&highlight=alc880]("http://www.ubuntuforums.org/showthread.php?t=187156&highlight=alc880")

[quote=chubuntu]

So I ended up downloading the 1.011 alsa driver, library, utilities, and oss from [http://www.alsa-project.org](http://www.alsa-project.org), basically:
479 cd /home/jim/downloads/alsa-dapper-1.0.11/
480 tar -xjvf alsa-driver-1.0.11.tar.bz2
481 tar -xjvf alsa-lib-1.0.11.tar.bz2
482 tar -xjvf alsa-oss-1.0.11.tar.bz2
483 tar -xjvf alsa-utils-1.0.11.tar.bz2
484 cd alsa-driver-1.0.11
485 ./configure --with-oss=yes --with-cards=hda-intel
486 make
487 make install
488 cd ../alsa-lib-1.0.11
489 ./configure
490 make install
491 cd ../alsa-oss-1.0.11
492 ./configure
493 make install
494 cd ../alsa-utils-1.0.11
495 ./configure
496 make install
497 alsaconf
498 shutdown -r now

[/quote]

and I went ahead. Installing this is almost impossible for a newbie like me:

performing lines 485 and 486 required the following:
- By synaptic install file libc6-dev and the sources of my current kernel.
- untar the sources and rename the directory to "linux"
- sudo apt-get install linux-headers-2.6.15-26-386
"make install" didn't work but "sudo make install" did.

I've given up on line 489:
I have the following error: configure: error: C++ preprocessor "/lib/cpp" fails sanity check.

If somebody can give me a hand, thank you very much. :)

---

### Post by we_r_disturbed on 2006-08-12
I was having the same error while trying to compile something else.

I solved mine with...

$ sudo apt-get install build-essential

Hope that helps

---

