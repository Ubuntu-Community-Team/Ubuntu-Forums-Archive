---
title: "NVidia driver on Ubuntu 6.06"
date: 2007-04-07
forum: Multimedia &amp; Video
---

### Post by VoidMain() on 2007-04-07
Hello.

I have tried to install and configure the nVidia driver to enable 3d acceleration in games. I had installed binary package 'nvidia-glx', then i typed 'sudo nvidia-glx-config enable' in terminal. I got the following error:
> Error: your X configuration has been altered.
This script cannot proceed automatically. If you believe that this
not correct, you can update the md5sum entry executing the following
command:
md5sum /etc/X11/xorg.conf | sudo tee /var/lib/x11/xorg.conf.md5sum
otherwise edit manually /etc/X11/xorg.conf to change the Driver section
from nv to nvidia.

Going by this message, i typed 'md5sum /etc/X11/xorg.conf | sudo tee /var/lib/x11/xorg.conf.md5sum'. Nvidia glx module loaded now, but when i restarted the X-server, it crashed. So i did the same things again in a safe mode (with xserver off) and typed 'startx' after that. Then I got an error:
> (WW) NVIDIA: No matching Device section for instance (BusID PCI:1:0:0) found
(EE) No devices detected.

Fatal server error:
no screens found

XIO: fatal IO error 104 (connection reset by peer) on X server ":0.0"
after 0 request (0 known processed) with 0 events remaining

Here is fragment of /var/log/Xorg.0.log file
> (--) PCI:*(1:0:0) nVidia Corporation unknown chipset (0x00f6) rev 162, Mem @ 0xea000000/24, 0xd0000000/28, 0xeb000000/24
(--) PCI: (2:8:0) unknown vendor (0x14f1) unknown chipset (0x8800) rev 5, Mem @ 0xe8000000/24

And fragment of xorg.conf after command 'md5sum /etc/X11/xorg.conf | sudo tee /var/lib/x11/xorg.conf.md5sum':
> Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon RV100 QY [Radeon 7000/VE]"
	Driver		"nvidia"
	BusID		"PCI:0:5:0"
EndSection

I do not know why identifier says that I have ATI Radeon. My graphic card is NVidia GeForce 6800 GS. And, as Xorg.0.log says, it's located on PCI:1:0:0, not on PCI:0:5:0. But if I make any change in xorg.conf,  I got again
> This script cannot proceed automatically. If you believe that this
not correct, [...]

I think problem is that there isn't any Device section which serves device on PCI:1:0:0 (my graphic card). But, as I said before, if I change PCI:0:5:0 to PCI:1:0:0 I got still the same error (it is above).

I hope i explained my problem clearly ;)

Please help me, because I spend about 5 hours trying to solve this and nothing helps.

---

