---
title: "Intel8x0 driver failes to compile for ALSA"
date: 2008-11-20
forum: Multimedia Software
---

### Post by kaniza on 2008-11-20
Hi all, 

I've been having the same problems with ALSA that it appears everyone else has, but unfortunately I seem to be running across a unique problem.

I used the Comprehensive Sound Problem Solutions Guide, and all is well for the most part. I ran 

sudo mkdir /usr/src/alsa
cd /usr/src/alsa
sudo apt-get install build-essential linux-headers-$(uname -r)
sudo wget [ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.14rc4.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.14rc4.tar.bz2)
sudo tar -xvjf alsa-driver-1.0.14rc4.tar.bz2
cd alsa-driver-1.0.14rc4
sudo ./configure --with-kernel=/usr/src/linux-headers-$(uname -r) --with-cards=intel8x0 --with-oss=yes
sudo make

And then I get these output errors:

make[1]: Leaving directory `/home/jody/alsa-driver-1.0.14rc4'
make -C /usr/src/linux-headers-2.6.25-2-386 SUBDIRS=/home/jody/alsa-driver-1.0.14rc4  CPP="gcc -E" CC="gcc" modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.25-2-386'
make[1]: Makefile: No such file or directory
make[1]: *** No rule to make target `Makefile'.  Stop.
make[1]: Leaving directory `/usr/src/linux-headers-2.6.25-2-386'
make: *** [compile] Error 2

As I am already in the alsa-driver folder, I assume the problem is happening with my header. I do have the complete 2.6.27 kernel, but for some reason my system refuses to boot into it (which is a side issue, so I'm sticking with 2.6.25 for now). 

Okay, main question is this: what needs to be done in order to allow the driver to fully compile?

Thank you in advance to anyone who answers!

---

### Post by psyke83 on 2008-11-20
The "Comprehensive" guide is hopelessly outdated; it doesn't even mention PulseAudio.

Do yourself a favour - forget about compiling ALSA drivers, and reinstall the version that already works:
```
$ sudo apt-get install --reinstall linux-image-`uname -a`
```

Follow the [PulseAudio Fixes]("http://ubuntuforums.org/showthread.php?t=789578") guide (and take some time to learn about PulseAudio from the FAQ and appendixes).

Check your PCM volume (many Intrepid users are noticing their PCM mixer getting reset to 0% and/or muted):
```
$ alsamixer -Dhw
```

And most important: ignore recommendations to remove PulseAudio/ALSA or install OSSv4. At least until you've attempted to configure PulseAudio correctly.

P.S. I'm using the snd-intel8x0 driver on my laptop, and it works fine with PulseAudio.

---

### Post by kaniza on 2008-11-20
Thank you so much for the answer, psyke83! :) I hate to continue with the stupid questions, but I did reinstall my kernel and followed the pulseaudio fixes (I ignored the asoundconf set-default-card command because I couldn't find any results for the Intel 82801DB-IGH4), but now when I try to get into the PA volume control, I get a 'connection refused' message, and then the window shuts down.

I tried aplay -l again, and it's giving me that 'no soundcards found' message once more. Am I that much of an idiot? What am I missing?

---

### Post by psyke83 on 2008-11-20
> **kaniza said:**
> Thank you so much for the answer, psyke83! :) I hate to continue with the stupid questions, but I did reinstall my kernel and followed the pulseaudio fixes (I ignored the asoundconf set-default-card command because I couldn't find any results for the Intel 82801DB-IGH4), but now when I try to get into the PA volume control, I get a 'connection refused' message, and then the window shuts down.

I tried aplay -l again, and it's giving me that 'no soundcards found' message once more. Am I that much of an idiot? What am I missing?

Your sound card isn't being detected correctly (possibly because the kernel modules are damaged or missing).

Did you reboot after reinstalling your kernel modules? Also check your kernel log (via dmesg) to see if there are any problems

---

### Post by kaniza on 2008-11-20
Okay, that's kind of what I figured. I will try to get the driver compiled into the module. I did do a reboot after reinstalling the kernel.

I think I'm just going to try module-assistant again to see if it will load the intel8x0 driver, as that seems to be the main problem.

Thank you for the help!

---

