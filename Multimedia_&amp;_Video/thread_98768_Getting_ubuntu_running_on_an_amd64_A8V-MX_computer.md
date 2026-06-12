---
title: "Getting ubuntu running on an amd64 A8V-MX computer (but sound doesn't work)"
date: 2005-12-04
forum: Multimedia &amp; Video
---

### Post by mathijs on 2005-12-04
This is an overview of steps I took to get ubuntu functional on a computer with a new amd64 A8V-MX motherboard (which has the VIA vt8251 chipset). (Skip to the last paragraph to see the current problem)

First, the ubuntu CD wouldn't boot from the Philips DVD/RW drive. Not only a CD-RW, but also a burnt CD-R and not even the official pressed CD would run. In all cases, there were "disk errors". Apparently, the Philips drive doesn't read correctly when DMA is disabled. 
As DMA support for the vt8251 chipset is not compiled in the ubuntu kernel, I installed a secondary cd-rom drive, and installed ubuntu from that. 
Ubuntu did not recognize the SATA harddisk I had, and my best bet to solve it was to replace the SATA disk by a regular ATA disk. I installed ubuntu onto that disk. (To get ubuntu working I disabled all unnecessary hardware in the BIOS, which was ACPI 2.0, APM, sound, serial & parallel ports). 
I then recompiled the kernel to support DMA, which is a trivial patch from [http://article.gmane.org/gmane.linux.ide/6599](http://article.gmane.org/gmane.linux.ide/6599)

Then I found out that X was behaving badly, with the text cursor being drawn multiple times in Mozilla & OpenOffice. The fix was to add 
Option "ShadowFB" "1"
to the device section of xorg.conf.

The next thing to get working was the network, which was to be set up via a sitecom wireless USB adapter. I found out that this is the orinoco chipset, but unfortunately, the orinoco-usb driver (from [http://folk.uio.no/oeysteio/orinoco-usb/](http://folk.uio.no/oeysteio/orinoco-usb/)) is not in standard kernels. So I recompiled the kernel again, and it worked.

Finally, I wanted to enable the sound. When I did that, the startup process froze at the start of X. By switching to a terminal and logging in, it could be continued by typing "killall esd". Therefore I disabled esd and chose ALSA as the default sound output. However, I can only play one second of sound and then it stops. Unfortunately I haven't found a solution to this problem.

---

### Post by frost242 on 2006-02-08
Hello,

I have the same problem with sound. I managed to get a working 64 bits system by upgrading the BIOS, the factory-installed BIOS being completly buggy.
I was bored about the onboard video chipset and finally put my old Radeon 7500 which works well in 2D but it's impossible to get 3D working.
And finally, same problem as you with the sound, even with a custom 2.6.15.2 kernel. Did you manage to get it run ?

Thanks in advance.
Thomas

---

### Post by alge on 2006-02-21
I got SATA running on my A8V MX with the patch 

  [http://grivell.home.comcast.net/via_ahci.patch](http://grivell.home.comcast.net/via_ahci.patch)

applied to a Dapper 2.6.15-15 kernel (I have both an amd64 and i386 Dapper installation on this box).

Currently I'm using two Seagate SATA disks with software RAID1 (md + raid1, not dmraid!). I didn't test the via Xorg driver very much, it seems to work. 

Only the sound problem left ...


Albrecht

---

