---
title: "unichrome xvmc"
date: 2005-10-19
forum: Multimedia &amp; Video
---

### Post by fragfutter on 2005-10-19
Has anyone directions to enable the mpeg2-hardware acceleration in the VIA CLE266 Chipset. 

(I have a epia board and would like to use it for a mythtv setup)

I managed to get dri working (at least my Xorg.0.log says so).

```

(II) VIA(0): direct rendering enabled
(II) VIA(0): [XvMC] Initialized XvMC extension.

```

Now i try to compile mplayer with XvMC support but it won't find the XvMC during configure-phase.

Any hints?

---

### Post by Lem on 2005-10-20
[QUOTE=fragfutter]
I managed to get dri working (at least my Xorg.0.log says so).
[/QUOTE]

Quite a few Epia users (myself included) struggling to get this far. How did you manage it?

---

### Post by Rinnan on 2005-10-20
I also got it working -- detailed instructions to follow. I will be creating a detailed HowTo today which will step you through Unichrome 3D, sensors, and accellerated mpeg2. One advantage of waiting will be that the kernel recompile step will need to include a patch for the vt1211 sensors module. So you'll have to compile your kernel again to put that in, if you want it, if you don't wait for the new instructions. On the other hand, one advantage of just doing this right now and forgetting about some utopian future is that you can get accellerated 3D RIGHT NOW! 

I know you've been waiting for this, Lem.

I just got 3D working today, about 16-17fps in planetpenguin-racer and about 250fps or so (in 32-bit 1280x1024) in glxgears.

Short instructions for the impatient expert:  (novice instructions take much longer to write but will be out later today).

#1: Set up your build environment (sudo apt-get install build-essential gcc-3.4) and then use this KernelHowto [https://wiki.ubuntu.com/KernelHowto]("https://wiki.ubuntu.com/KernelHowto") from Ubuntu's wiki to build your own kernel. When the kernel HowTo asks you to configure your kernel, use the /boot/config-<your kernel version> file to configure it (cp /boot/config-<your kernel version> /usr/src/linux/.config && make oldconfig). Then do a "make menuconfig" and change the processor type to your CPU type ("Processor type and features / Processor Family / <choose your own CPU here>"). *Do not delete the /usr/src/linux softlink, even though the HowTo tells you to.* At least, not yet. You are likely to want to follow the instructions and make your own .deb package file, then back it up somewhere. You don't want to be doing this often, it takes a *long* time. Now is a good time to make any other kernel changes you want to make, but I kept the defaults (except to turn kernel preemption on).
#2:  Boot off of this new kernel.
#3: Use the unichrome-drm script from epiawiki.org (called "                   [             drm-unichrome-install_v6.0]("http://www.epiawiki.org/wiki/tiki-download_file.php?fileId=24")"). You must create a softlink (ln -s /usr/bin/makedepend /usr/X11R6/bin/makedepend) and install three -dev packages (sudo apt-get install libdrm-dev libxpat1-dev libx11-dev).

The script will give you errors, after all it was made for Gentoo, not Ubuntu, but it works. I'm working to modify it to work without errors (mostly just to make it prettier) with Ubuntu. This should result in the newer instructions being slightly simpler.

At the end, type "sudo depmod -ae" (need to test if this is necessary), then "sudo modprobe via" -- finally, reset your X (this is necessary), and there ya go.

My motherboard: EPIA MII 12000.

Erik

---

### Post by Lem on 2005-10-21
I understand most of the above, but as I've not done a kernel recompile before I await the simple destructions with baited breath.

Cheers dude.. ;)

---

### Post by fragfutter on 2005-10-21
I wrote a sum of my installation. But i'm stil missing the mpeg2 acceleration (with xvmc)

[http://plone.held-im-ruhestand.de/software/ubuntuunichrome](http://plone.held-im-ruhestand.de/software/ubuntuunichrome)

---

### Post by Rinnan on 2005-10-21
I've built a new .deb file you can just download and install with "sudo dpkg -i <the name of it>.deb" and reboot. I've tested it and it works (so far :razz:).

I just need a place to put it on the internet so people can download it. My machine I use for testing a lot -- it's rebooted fairly often as I play with new kernels and so on. And the other machine is a laptop -- PPC at that.

See [this thread]("http://www.ubuntuforums.org/showthread.php?t=80248").

Erik

BTW, fragfutter, that link appears to be down?

P.S. Lem, what motherboard exactly do you have?  Specifically I need to know the CPU, and if it's the older (CLE266) or newer (Unichrome Pro) chipset.

---

### Post by fragfutter on 2005-10-22
the link is up and running. Monitoring reports no outings in the last 30 days.

if you want to i can host the deb files on a server located in germany.

Did you manage to get the xvmc extension working with mplayer or xine? The reason i'm asking is, that i have 3d anx xv capabilities with my setup but playing a mpeg2 (working flawless) still results in 80% cpu load. With hardware decoding it should be around 40%.

---

### Post by Lem on 2005-10-22
[QUOTE=Rinnan]
P.S. Lem, what motherboard exactly do you have?  Specifically I need to know the CPU, and if it's the older (CLE266) or newer (Unichrome Pro) chipset.[/QUOTE]

I have an M10000 with CLE266 - I beleive only the SP boards have unichrome pro?

PS. I can host the deb for you if you wish.

---

### Post by Rinnan on 2005-10-22
Cool, okay, I'll send the deb (kernel-image, I assume is the most desireable one) to you.  

Here are the debs and their sizes:

```
2837536 kernel-doc-2.6.13-ck8.20051020_10.00.Custom_all.deb
5448484 kernel-headers-2.6.13-ck8.20051020_10.00.Custom_i386.deb
15546092 kernel-image-2.6.13-ck8.20051020_10.00.Custom_i386.deb
38580556 kernel-source-2.6.13-ck8.20051020_10.00.Custom_all.deb
``` 
Meanwhile, I'm writing a script which, when run, will do everything for you (install all packages, download all source, build it, install it, and ask you to reboot. It won't reboot for you :razz:).

Still waiting on mpeg2 -- want to finish 3D first -- don't worry it's all going to happen. 

This kernel might still be useful to you, fragfutter, since it contains the (I believe excellent) Con Kolivas patches.

---

### Post by fragfutter on 2005-10-23
I will stick to the vanilla kernel.

I did a lot of kernel patching the last two years, but i now think that it is fast enough for me that some features will be implemented half a year later (Except patches to support hardware).

---

### Post by Lem on 2005-10-25
(edit) No panic.. sorted problem!

---

### Post by k4p0w3r on 2005-12-07
Sorted. I made a wiki for all Epia fans:

[https://wiki.ubuntu.com/ViaEpiaDriHowto](https://wiki.ubuntu.com/ViaEpiaDriHowto)

---

### Post by Beej on 2006-03-02
Just to let you all know I'm running dapper on my mini-itx board which has the via cle266 chipset. Dri is working out of the box, as  is dvd playback, which I assume means that xvmc support is included!

---

