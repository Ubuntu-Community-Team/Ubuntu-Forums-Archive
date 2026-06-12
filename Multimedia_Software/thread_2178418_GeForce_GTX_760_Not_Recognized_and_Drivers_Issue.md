---
title: "GeForce GTX 760 Not Recognized and Drivers Issue"
date: 2013-10-03
forum: Multimedia Software
---

### Post by rdJB8wd on 2013-10-03
I have a new system which came with Ubuntu 13.04 installed. The system uses a new GTX 760 video card. But for some reason, my system does not seem to recogize this card. I have sent a few weeks on trying to fix this (carefully reading hints and multiple fora) and need help. Does anyone have any ideas for fixing this issue (or can at least replicate it)?

This is the current state of my system and direct output.
```
lspci | grep VGA 
01:00.0 VGA compatible controller: NVIDIA Corporation Device 1187 (rev a1)
```

```
sudo lshw -c video
  *-display               
       description: VGA compatible controller
       product: NVIDIA Corporation
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:48 memory:f6000000-f6ffffff memory:e8000000-efffffff memory:f0000000-f1ffffff ioport:e000(size=128) memory:f7000000-f707ffff
```

The screenshot of Software & Updates shows 
[ATTACH=CONFIG]246703[/ATTACH]

Nowhere does the GTX760 card appear--and the information seems to indicate some other driver is in use.

**What I Tried**
I have tried several things over the past few weeks. I have tried using the drivers for

the official Ubuntu packages
nvidia-current
nvidia 304
nvidia 310
nvidia 313
nouveau

then I tried installing the NVidia 3.25 driver x64 directly from NVidia. This failed completely with kernel issues and I had to recover from that problem and uninstall the direct proprietary drivers.

then I tried the adding the X-SWAT ppa and tried
nvidia 319 (which seems to indicate it should now recognize the GTX 760)

No change.

I cleared the X-swat repository using 
```
sudo ppa-purge ppa:ubuntu-x-swat/x-updates
```

Then I added the x-edgers PPA and tried 
nvidia 319
nvidia 325 (which seems to support the GTX 760)

As shown above (this is the current status of my system), it doesn't seem like the card is recognized.

I have spent the last few weeks on this and really cannot figure out what more to do.

**Wh****y's So Much Time?**
Unfortunately, there seems to be a bug with virtual terminals gnome-terminal or mate-terminal and this card that freezes terminal display output and the underlying programs randomly. In other words, when a program (from launcher or directly run from the terminal) runs, the programs randomly stops. I run machine learning algorithms that need to run for hours in some cases displaying output from time to time. This problem is maddening because the learning randmoly stops and you ned to manually restart it. That is why I have spent so much time on this issue--to hopefully, resolve this underlying problem.

**Ubuntu Version**
13.04 x64

**Desktops tried:**
Ubuntu Default
GNOME3
MATE 1.6.1

**System**
EVGA GeForce GTX 760 2GB
i7 4770
32GB Memory

---

### Post by Bucky Ball on 2013-10-03
*Thread moved to **Multimedia & Video**.*

---

### Post by oldfred on 2013-10-03
I thought the very newest nVidia driver needed the very newest kernel which is in the soon to be released 13.10. But it still is beta so you then are a tester if you decide to try 13.10.

Several users with new Haswell systems have used 13.10 and reported it running well. Not sure any had your video card.

Open source driver comparision, soon to release closed source comparison also.
 Open Source only drivers - 16-Way Graphics Card Comparison On Open-Source Linux
[http://www.phoronix.com/scan.php?page=article&item=haswell_linuxgpu_16way&num=1](http://www.phoronix.com/scan.php?page=article&item=haswell_linuxgpu_16way&num=1)

 Intel "Haswell" System 76 Iris Pro Linux Graphics Yield Some Wins Against Windows
[http://www.phoronix.com/scan.php?page=article&item=intel_irispro_linwin&num=1](http://www.phoronix.com/scan.php?page=article&item=intel_irispro_linwin&num=1)
NVIDIA's Linux Driver On Ubuntu Is Very Competitive With Windows 8
[http://www.phoronix.com/scan.php?page=article&item=nvidia_windows8_geforce&num=1](http://www.phoronix.com/scan.php?page=article&item=nvidia_windows8_geforce&num=1)
Linux 3.2 To 3.8 Kernels With Intel Ivy Bridge Graphics
[http://www.phoronix.com/scan.php?page=article&item=intel_linux32_38&num=1](http://www.phoronix.com/scan.php?page=article&item=intel_linux32_38&num=1)

---

### Post by rdJB8wd on 2013-10-18
Thank you oldfred.

Actually, after quite a bit of work, the xorg-edgers 325 driver did properly recogize the GTX 760 on Ubuntu 13.04. Today, I upgraded to 13.10. The GTX 760 caused problems again, but the default nvidia-319-updates driver included in Ubuntu 13.10 does seem to work and does appear recognized now (Installing it can be a problem and I could not get nvidia-settings to properly recognize the card at all after installing 319. I had to uninstall 319, restore my xorg.conif file in etc/X11, and then reinstall 319 from Software & Updates (not from Synaptic). Weird but eventually the 319 driver worked. (The error I kept getting was in Nvidia Settings which indicated that I was not using a Nvidia driver and needed to run nvidia-xconfig as root. THIS DID NOT WORK. Again, I needed to uninstall and then weirdly install by switching the driver--which remained after the uninstall--from Software & Updates.)

---

### Post by optimusprime198630 on 2013-12-10
I have a dual boot windows 8/ Ubuntu 12.04 system with EVGA Gtx 760(I have a Haswell processor). I have been unable (for the past 2 months) to get the video card to work on linux. I will post what hardware I am using. It would be great if you would post in a little more detail how you got it to work. By the sounds of things the first step would be to upgrade to Ubuntu 13.

I have

i5-4760K 3.4 GHz
EVGA GTX 760
8 Gb of ram
120 Gb SSD - SamSung
2-TB Storage 

So just to clarify what I have to do right now to run Ubuntu is I have to switch the video cable from the graphics card port to the video output on the mother board
because the graphics card is not recognized. Any way any help would be greatly appreciated!

---

### Post by codenine75a on 2013-12-10
Don't be shy.  Download the latest Linux drivers from Nvidia directly.  They are binaries that you may have to find a way to drop to a pure console environment to install, but it is worth the hard work.  I think you have to drop the OS down to single user mode and install them.  It was a few years since I worked with them.

---

### Post by oldfred on 2013-12-10
I think both Intel drivers and nVidia drivers have updates that only really work with the new kernel in 13.10 for Haswell as that is a very new system. The next 12.04.4 in Jan should then be updated also.

       New Intel driver installer (only with 13.04)
[http://www.phoronix.com/scan.php?page=news_item&px=MTQyNTQ](http://www.phoronix.com/scan.php?page=news_item&px=MTQyNTQ)


 Updates to nVidia Prime with 14.04 (only)
[http://www.phoronix.com/scan.php?page=news_item&px=MTU0MDI](http://www.phoronix.com/scan.php?page=news_item&px=MTU0MDI)
Newest nVidia Prime with 13.10 testing may run hot, but option to bumblebee
[http://www.webupd8.org/2013/08/using-nvidia-graphics-drivers-with.html](http://www.webupd8.org/2013/08/using-nvidia-graphics-drivers-with.html)

---

