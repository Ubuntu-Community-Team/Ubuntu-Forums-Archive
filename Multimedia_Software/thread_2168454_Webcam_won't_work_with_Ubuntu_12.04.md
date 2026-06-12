---
title: "Webcam won't work with Ubuntu 12.04"
date: 2013-08-17
forum: Multimedia Software
---

### Post by 4WYnQex on 2013-08-17
Hi guys,

my webcam refuses to work with any application: skype, guvcview, cheese, etc.

The webcam is supposed to be supported: Microsoft Lifecam VX-5000

When I run guvcview, I get the following: 'Guvcview error: Unable to allocate Buffers'. If I run gstreamer-properties and I try to test it, I get: Video for Linux 2 (v4l2): Could not get buffers from device '/dev/video0'

I've been trying different things, but I feel I'm going around in circles. Any help would be appreciated!

Thanks in advance.

---

### Post by gordintoronto on 2013-08-18
Could you describe your computer? Laptop or desktop? CPU? Memory? Video adapter? Perhaps you could copy/paste the output from these commands:
lsusb
lspci

When I run Cheese, I have to wait almost a minute for my (cheap Chinese) webcam to fire up, then it works perfectly. The webcam shows up under Preferences as /dev/video0

---

### Post by 4WYnQex on 2013-08-21
Hi,

sorry about the delay in responding. It's a fairly old desktop, but I've had this webcam work in a previous Ubuntu installation. I honestly have no idea what is wrong now.  Here's the output of those commands

luis@desktop:~$ lsusb
Bus 001 Device 004: ID 1058:0748 Western Digital Technologies, Inc. 
Bus 002 Device 002: ID 045e:0728 Microsoft Corp. 
Bus 004 Device 002: ID 413c:3012 Dell Computer Corp. Optical Wheel Mouse
Bus 004 Device 003: ID 413c:2003 Dell Computer Corp. Keyboard
Bus 005 Device 002: ID 04a9:220d Canon, Inc. CanoScan N670U/N676U/LiDE 20
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
luis@desktop:~$ 
luis@desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02)
00:19.0 Ethernet controller: Intel Corporation 82562V-2 10/100 Network Connection (rev 02)
00:1a.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
00:1d.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IR (ICH9R) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801IR/IO/IH (ICH9R/DO/DH) 4 port SATA Controller [IDE mode] (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801I (ICH9 Family) 2 port SATA Controller [IDE mode] (rev 02)
01:00.0 VGA compatible controller: NVIDIA Corporation G98 [GeForce 8400 GS] (rev a1)
02:01.0 Multimedia video controller: Conexant Systems, Inc. CX23418 Single-Chip MPEG-2 Encoder with Integrated Analog Video/Broadcast Audio Decoder
luis@desktop:~$

Thank you!

---

### Post by gordintoronto on 2013-08-21
Off the wall suggestion: unplug your scanner and reboot.

---

### Post by 4WYnQex on 2013-08-22
No luck...I also unplugged the external hard drive, and the printer was already unplugged.

Here's the updated lsusb:

luis@desktop:~$ lsusb
Bus 002 Device 002: ID 045e:0728 Microsoft Corp. 
Bus 004 Device 002: ID 413c:3012 Dell Computer Corp. Optical Wheel Mouse
Bus 004 Device 003: ID 413c:2003 Dell Computer Corp. Keyboard
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
luis@desktop:~$

---

### Post by gordintoronto on 2013-08-22
Sorry, I'm out of pie. "It should just work."

How much memory in this computer? I have found that 512 MB is just enough to generate a multitude of weird issues.

---

### Post by 4WYnQex on 2013-08-22
It has 4GB:

luis@desktop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          4035       1193       2842          0         69        547
-/+ buffers/cache:        576       3458
Swap:         9536          0       9536
luis@desktop:~$

---

### Post by 4WYnQex on 2013-09-01
OK, I was finally able to find a solution for this issue: increase the vmalloc size the kernel uses to 512MB:

edit grub.cfg: gksudo gedit /etc/default/grub
then add vmalloc=512m to this line: GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
so that it looks like: GRUB_CMDLINE_LINUX_DEFAULT="quiet splash vmalloc=512m"
save grub.cfg

and then run 'sudo update-grub'

reboot

Hopefully this helps other people with the same issue.

---

