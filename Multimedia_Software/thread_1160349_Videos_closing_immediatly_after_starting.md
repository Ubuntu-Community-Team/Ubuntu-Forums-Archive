---
title: "Videos closing immediatly after starting"
date: 2009-05-15
forum: Multimedia Software
---

### Post by cyberknight72 on 2009-05-15
I have managed to configure Gnome Mplayer without issue.  I can open videos etc.  However if I use any other program VLC or Miro for example, the video starts and immediately closes the window.  I have the restricted formats installed.  In Gnome Mplayer I am using the X11 driver, okay good to go there...  Did not see where to set it in VLC or Miro?  Problem only arose after upgrading to 9.04 from 8.10 (I have wiped the system since and done a clean install with 9.04)...

Thanks for any help!

---

### Post by xzero1 on 2009-05-15
Try running vlc from a terminal. This will give you more information as to what is happening.

---

### Post by cyberknight72 on 2009-05-15
ran VLC from terminal with the following error:

X Error: BadAlloc (insufficient resources for operation) 11
  Extension:    132 (Uknown extension)
  Minor opcode: 19 (Unknown request)
  Resource id:  0x4400005

I have audio but no video.  I tried to play an AVI.

Ideas?  Is this a video card memory issue?  RAM issue?

Thanks!

---

### Post by cyberknight72 on 2009-05-15
Finally stopped scrolling the error...

[????????] x11 video output error: X11 request 132.19 failed with error code 11:
 BadAlloc (insufficient resources for operation)

Anyone have ideas?

Thanks!

---

### Post by xc3RnbFO8P on 2009-05-15
What is your computer spec.?

---

### Post by cyberknight72 on 2009-05-15
Here is a bit information.  Is it a possible issue with the Intel Graphics Controller?  I have seen a little bit of traffic on it after upgrading to 9.04.

Pentium 4 2.6GHZ
1GB RAM

david@office:~$ lspci
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
01:07.0 Multimedia audio controller: Creative Labs CA0106 Soundblaster
01:0c.0 Ethernet controller: Intel Corporation 82540EM Gigabit Ethernet Controller (rev 02)

---

### Post by xc3RnbFO8P on 2009-05-15
Try this:
> Workaround to get it working: open gstreamer-properties. Then, Video tab, Default Output section. Change the Plugin from "Autodetect" to "X Window System (No Xv)" and close. This way, totem will play any video format, but the other players still not working.
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/354688]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/354688")

---

