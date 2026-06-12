---
title: "Mythbuntu on EPIA SP1300"
date: 2007-11-07
forum: Mythbuntu
---

### Post by Mr_Dub on 2007-11-07
Hi. Has anyone managed to ge Mythbunti 7.1 running smoothly on an EPIA SP1300 (with 1GB RAM, 250 GB SATA HDD)? I've got the screen res (VGA output) working nicely at 1360x768 but my problem is getting the XvMC working properly (I think). Kaffeine reports that XvMC won't init and uses 100% CPU with jerky video, Xine appears to work using the xxmc option instead of xvmc with quite low CPU but still jerky, and Myth reports frequent skipping of frames to keep in sync (using the VIA XvMC option) whilst using anywhere between 40-60% CPU. I'm using the latest openchrome driver (installed using the script here ([http://ubuntuforums.org/showthread.php?t=485646](http://ubuntuforums.org/showthread.php?t=485646)). Any help much appreciated!

---

### Post by rhp on 2008-01-09
After installing mythbuntu on an EPIA M1000, I've run into problems with XvMC as well :-( ... It would be great if this would work, since I had mythdora running fine before.

---

### Post by ozybushwalker on 2008-01-09
I don't know what chipset is on your motherboard. Its possible you have set your display resolution to exceed the hardware acceleration capability of the chipset.

I have Mythbuntu installed on a GA-PCV2 motherboard which has a CLE-266. I ran into problems with high CPU usage. I suspect there were a number of causes and that reducing the display resolution to within the documented hardware acceleration capabilities of the CLE-266 helped. Some other tweaks helped as well. There's more information in a bug report at [https://bugs.launchpad.net/mythbuntu/+bug/179634]("https://bugs.launchpad.net/mythbuntu/+bug/179634")

If I recall correctly, it was pretty easy to set the display resolution too high, but rather a challenge to get it down.

---

### Post by rhp on 2008-01-11
I've set the display resolution to 720x576Noscale for use on a PAL TV. I can't believe that would be too high (and it was ok in mythdora before).

---

### Post by richard.e.morton on 2008-12-15
I have a similar issue with mythbuntu 8.10 with an EP13000. Another forum
says
"Made sure that the file /etc/X11/XvMCConfig has the line “libviaXvMC.so.1&#8243; in it." - [http://sm3rt.wordpress.com/2008/07/21/mythtv-on-via-epia-sp13000/](http://sm3rt.wordpress.com/2008/07/21/mythtv-on-via-epia-sp13000/)

so I put that in it. and still no improvement with tv playback or video playback. I have res set to something like 1200x800 (widescreen monitor).

Anyone got this to work yet? As I say it works with Fedora Core 7 (FC7) and Myth 0.20

Thanks for any help

Rich

---

