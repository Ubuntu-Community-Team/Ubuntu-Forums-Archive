---
title: "NVidia 7600 GS random X lockup"
date: 2006-10-02
forum: Multimedia &amp; Video
---

### Post by benguin on 2006-10-02
Hi there,
I have searched the forum for answers, tried a few and none of them worked, so I'm posting this with the hope that I'll get some advice that might finally work!

So here's the story. I used to have an (old) NVidia GeForce4 MX 400 card, on the AGP bus, and I decided to buy a newish card, with a more powerful GPU for some gaming and more importantly using a powerful gpu in some scientific computation. So I get myself a BFGTech produced GeForce 7600 GS AGP, with 512 megs of video ram. I take out the old card, which, by the way ran without a hitch, and put the new one. Power up, cool, no problems. For 5 minutes. Then the nightmare began. X just started locking up at random moments. Not even during gaming; even for example browsing the Ubuntu forums I'd get X locking up. At this point I had the plain-vanilla xorg.conf with one line (Driver "nvidia") for the driver and no "Option" lines. So I decide to reinstall Dapper, hoping a clean install will solve the problem. No luck there either. The "nv" driver does not work, and vesa is extremely slow, but at least it works (like right now, I'm using vesa). 

I looked up the information on the different files under /proc/driver/nvidia. Seems like AGP is enabled, side band addressing is not, but fast write is. Bios and card ID are properly reported. GPU core is at 40 degrees celsius, and CPU is at 32 degrees. The system spec is given below.

CPU: AMD Athlon 64 3200+
OS: Ubuntu Dapper 32-bit edition
RAM: 1 GB
M/B: Asus A8V-Deluxe (Via KT800pro chipset)
AGP: NVidia 7600 GS, 512MB, BFGTech 
Driver Version: 1.0.8762 (Driver that comes with Dapper)

Any suggestions how to go about solving this lockup issue? If anyone wants any more log outputs or something, I'd be glad to post those. It bugs me to no extent that I have zero idea what's causing this. How could I at least see the system log or something when X locks up on me?

Thanks a lot!

-J-

---

### Post by tseliot on 2006-10-03
> **benguin said:**
> Hi there,
I have searched the forum for answers, tried a few and none of them worked, so I'm posting this with the hope that I'll get some advice that might finally work!

So here's the story. I used to have an (old) NVidia GeForce4 MX 400 card, on the AGP bus, and I decided to buy a newish card, with a more powerful GPU for some gaming and more importantly using a powerful gpu in some scientific computation. So I get myself a BFGTech produced GeForce 7600 GS AGP, with 512 megs of video ram. I take out the old card, which, by the way ran without a hitch, and put the new one. Power up, cool, no problems. For 5 minutes. Then the nightmare began. X just started locking up at random moments. Not even during gaming; even for example browsing the Ubuntu forums I'd get X locking up. At this point I had the plain-vanilla xorg.conf with one line (Driver "nvidia") for the driver and no "Option" lines. So I decide to reinstall Dapper, hoping a clean install will solve the problem. No luck there either. The "nv" driver does not work, and vesa is extremely slow, but at least it works (like right now, I'm using vesa). 

I looked up the information on the different files under /proc/driver/nvidia. Seems like AGP is enabled, side band addressing is not, but fast write is. Bios and card ID are properly reported. GPU core is at 40 degrees celsius, and CPU is at 32 degrees. The system spec is given below.

CPU: AMD Athlon 64 3200+
OS: Ubuntu Dapper 32-bit edition
RAM: 1 GB
M/B: Asus A8V-Deluxe (Via KT800pro chipset)
AGP: NVidia 7600 GS, 512MB, BFGTech 
Driver Version: 1.0.8762 (Driver that comes with Dapper)

Any suggestions how to go about solving this lockup issue? If anyone wants any more log outputs or something, I'd be glad to post those. It bugs me to no extent that I have zero idea what's causing this. How could I at least see the system log or something when X locks up on me?

Thanks a lot!

-J-
Try point 4 of the Problems Section of my guide and see if anything changes:
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper)

---

### Post by benguin on 2006-10-03
Thanks tseliot. I didn't try that though, it gave me the impression that hardware acceleration would be disabled by those changes you suggsted. Or am I wrong on that?

I wanted to do a follow up, thankfully a positive one. The problems I was facing seem to be taken care of by installing the beta nvidia driver (9625). I had to patch the sources manually with a patch provided at the nvidia linux support forum. I've played bzflag, quake 4 demo, and things seem to run very well indeed. Just in case someone else runs into the same set of problems, here's how I installed the beta drivers on Dapper.

1. Follow the Ubuntu pre-installation advice as seen here, at the bottom of the page: [Disabling nvidia drivers from linux restricted modules]("http://www.nvnews.net/vbulletin/showthread.php?t=72490")

2. Download the 9625 beta drivers from nvidia.com.

3. Extract the files from the package by running with the --extract-only option. 

4. Download the patch that can be found on the second page of this topic: [Nvidia Linux beta drivers]("http://www.nvnews.net/vbulletin/showthread.php?t=77021"). The patchfile is called **NVIDIA_kernel-1.0-9625-NOSMBUS.diff.txt**

5. Change directory to the uncompressed nvidia driver package root and patch the sources: 
```
patch -p0 < /path/to/patchfile
```

6. Without X running, run **nvidia-installer** as root from that directory. 

Please make sure you have all the prerequisite packages installed before trying this. The patch mentioned here disables SMBus support, with which (SMBus) I was getting a black screen at bootup. I still don't know what was wrong initially, but looks like the (patched)driver is indeed working well.


Hope this is sorted out before Edgy hits first release.

Now, it's time I tried compiz on this :eek:

---

