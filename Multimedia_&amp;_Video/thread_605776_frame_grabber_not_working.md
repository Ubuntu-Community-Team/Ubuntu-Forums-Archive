---
title: "frame grabber not working"
date: 2007-11-07
forum: Multimedia &amp; Video
---

### Post by curley_sue on 2007-11-07
OK, it has been several days and I cannot seem to find the answer.

I need to capture images from a video camera to the desktop as part of an experiment in Fluid Mechanics.

My hardware:
COHU Solid state camera
Rio frame grabber ( manufacturer Ellips) [http://www.ellips.nl/framegrabbers_m...grabber_2.html](http://www.ellips.nl/framegrabbers_m...grabber_2.html)

lspci


00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
00:07.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
00:0c.0 Multimedia audio controller: Yamaha Corporation YMF-740C [DS-1L Audio Controller] (rev 03)
00:0e.0 VGA compatible controller: ATI Technologies Inc 3D Rage II+ 215GTB [Mach64 GTB] (rev 9a)
00:0f.0 Ethernet controller: 3Com Corporation 3c905B 100BaseTX [Cyclone] (rev 30)
00:10.0 Multimedia controller: Philips Semiconductors SAA7146 (rev 01)

(I guess the last one is the frame grabber)

I have tried
sudo modprobe saa7146
sudo modprobe v4l2-common
sudo modprobe v4l1-compat

and got no /dev/video0

so I tried
sudo /etc/init.d/udev restart

but still no good news.

I will appreciate whatever help you can give

supplement:
~$ sudo modprobe saa714
saa7146     saa7146_vv  
~$ sudo modprobe saa7146
~$ lsmod |grep -i ssa
~$ dmesg |grep -i saa
~$ lspci -x -d 1131:7146
00:10.0 Multimedia controller: Philips Semiconductors SAA7146 (rev 01)
00: 31 11 46 71 04 00 80 02 01 00 80 04 00 7b 00 00
10: 00 94 00 f4 00 00 00 00 00 00 00 00 00 00 00 00
20: 00 00 00 00 00 00 00 00 00 00 00 00 4c 45 01 00
30: 00 00 00 00 00 00 00 00 00 00 00 00 09 01 0f 26

---

