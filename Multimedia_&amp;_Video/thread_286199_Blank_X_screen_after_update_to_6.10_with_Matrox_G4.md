---
title: "Blank X screen after update to 6.10 with Matrox G400"
date: 2006-10-27
forum: Multimedia &amp; Video
---

### Post by ManfredU on 2006-10-27
Since the update from 6.06 to 6.10 X is no longer working for me. The graphics adapter is a Matrox G400 which was working without problems with all previous Ubuntu versions. The problem is: X seems to start but the monitor remains black, just the following on screen error message is displayed (The modelines in the log file look fine):


Monitor IBM P260
-----------------
INPUT 18.3 KHz / 15 Hz
OUT OF SCAN RANGE
CHANGE SIGNAL TIMING


xorg.conf
----------------
[attached]


Xorg.0.log
----------------
[attached]



/var/log/messages
-----------------

[17179610.880000] matrox_w1 0000:01:00.0: Matrox G400 GPIO transport layer for 1-wire.

[17180007.772000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 177

[17180007.776000] [drm] Initialized mga 3.2.1 20051102 on minor 0
[17180007.776000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[17180007.776000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 1x mode
[17180007.776000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 1x mode


lspci
-----------------
01:00.0 VGA compatible controller: Matrox Graphics, Inc. G400/G450 (rev 04)

---

### Post by hikaricore on 2006-10-27
I have the same card and X is working, but direct rendering was broken in the upgrade.

j2@j2-cs:~$ glxinfo
name of display: :0.0
libGL warning: 3D driver claims to not support visual 0x4b

Are you using the MGA driver for yours?

---

### Post by ManfredU on 2006-10-27
Yes, I'm using the MGA driver:

(II) LoadModule: "mga"
(II) Loading /usr/lib/xorg/modules/drivers/mga_drv.so
(II) Module mga: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.4.1
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 1.0

$ glxinfo
name of display: :0.0
libGL warning: 3D driver claims to not support visual 0x4b

Why was it broken? What did you do to get it working for you?

---

### Post by hikaricore on 2006-10-27
No I was using the mga driver before, and direct rendering was working right after install, I was just checking to see if we were using the same driver.  Be sure that you have:
```
Option  "UseFBDev"   "false"
```

In your graphics card device line.

to get to your conf file do from command line:
```
sudo pico /etc/X11/xorg.conf
```

X seems to either crash or not load with frame buffer enabled.  I have both the dual port and single port model of the G400 (the single might go by a different name but it's basicly the same card) and as long as frame buffer is disabled the card works.  But I have the direct rendering issue once X is loaded.  The comp I have this card in is at my office so I won't be able to check any more info until moday.  Hopefully you're problem is solved by then tho. :)

---

### Post by pjssilva on 2006-10-28
This is a bug in the mga driver that comes with Xorg in edgy. It is a shame that Edgy was released with such a regression even after the bug was reported and the fix known. See:

[https://launchpad.net/distros/ubuntu/+source/xserver-xorg-video-mga/+bug/58721](https://launchpad.net/distros/ubuntu/+source/xserver-xorg-video-mga/+bug/58721)

I have compiled the new driver from Debian unstable to make my system usable. I have changed the dependencies to allow for a clean install in edgy. If you want, download it here:

[http://www.ime.usp.br/~pjssilva/xserver-xorg-video-mga_1.4.2.dfsg.1-1_i386.deb](http://www.ime.usp.br/~pjssilva/xserver-xorg-video-mga_1.4.2.dfsg.1-1_i386.deb)

If you don't want to use a third party compiled driver download the source from Debian and edit the dependencies to make it depend on xserver-xorg-core (>= 1:1.1.1), instead of the newer version of xserver-xorg-core in Debian unstable.

What is amazing is that for such a major bug, first reported on September 3rd, the importance is still classified as "Undecided" :-(

---

### Post by sp4rd on 2006-10-28
Yeah, you need at least 1.4.2 of the xorg mga driver to get dri working with a g450.  I have both a g400 and g450.  It worked with the g450 but there still seems to be problems with my g400(no output with glxgears,probably a locking issue still with g400).  Hopefully this is fixed soon because I want to upgrade my dapper to edgy with compiz/aiglx.

---

### Post by euphro on 2006-10-28
I've got a G400 and the same problem. Thanks pjssilva, I will install your driver and give it a go.  I've been a bit stuck since I can only access Edgy via the console.  Manually editing sources.list to include the Debian unstable repositories is not something that I relished.  I hope this gets fixed soon.

---

### Post by pjssilva on 2006-10-29
A hint to euphro and other that are not very used to the magic of command line interfaces and Debian/Ubuntu package system. To install my driver is to download the file from the link in my message above, using a utility like wget, and then type the following line on the console:

dpkg -i xserver-xorg-video-mga_1.4.2.dfsg.1-1_i386.deb

After that, reboot and, hopefully, X will work just fine.

---

### Post by euphro on 2006-10-30
Thanks pjssilva, that solved the problem!  For users not familar with the console, of course you'll have to add "sudo" in front of the command outlined by pjssilva.

After downloading the file to another PC, I had to burn it to DVD so I could transfer it to the afflicted machine (etc/fstab had no reference to my floppy drive in it) then mount the DVD drive (mount /mnt/cdrom0) before I could run dpkg, but it seems to be working so far. :)

---

### Post by grahams on 2006-11-03
Thanks for the post of this. I ran into the same issue and your mga driver cures my woes.

---

### Post by AndyC_772 on 2007-02-25
Today I've tried to completely reinstall Edgy from scratch on my desktop PC, which has a Matrox G400 card.

I do remember having to install a modified mga driver before, and it fixed the problem. However, having just reinstalled (using the alternate Edgy install CD), even forcing an install of the modified xserver-xorg-video-mga driver hasn't helped. My X server still completely fails to start, complaining about having no valid video modes.

Does this mean it's actually not possible to install Edgy from scratch on a machine with a G400? (Previously I'd installed Dapper and then upgraded, but I'd rather not go that route unless I have to).

Any suggestions welcome, please - I'm getting frustrated that such an obvious and serious bug should have been allowed to slip through... :(

---

