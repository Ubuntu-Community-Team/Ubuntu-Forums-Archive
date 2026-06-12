---
title: "Suddenly unable to play multimedia files with sound."
date: 2008-08-01
forum: Multimedia Software
---

### Post by robfindlay on 2008-08-01
I'm running Hardy Heron and I have a problem where I'll suddenly be unable to play multimedia files with sound until I reboot the system. 

I'm half convinced that certain web pages that play video automatically are locking the sound card or another multimedia device. 

Here's my LSPCI:
00:00.0 Host bridge: ALi Corporation M1647 Northbridge [MAGiK 1 / MobileMAGiK 1] (rev b0)
00:01.0 PCI bridge: ALi Corporation PCI to AGP Controller
00:02.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:04.0 IDE interface: ALi Corporation M5229 IDE (rev c4)
00:07.0 ISA bridge: ALi Corporation M1533/M1535 PCI to ISA Bridge [Aladdin IV/V/V+]
00:0a.0 Ethernet controller: D-Link System Inc RTL8139 Ethernet (rev 10)
00:0b.0 Multimedia audio controller: Ensoniq 5880 AudioPCI (rev 02)
00:0c.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:0c.3 USB Controller: ALi Corporation USB 2.0 Controller (rev 01)
00:0d.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)
00:0e.0 RAID bus controller: HighPoint Technologies, Inc. HPT366/368/370/370A/372/372N (rev 05)
00:11.0 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
01:00.0 VGA compatible controller: nVidia Corporation NV20 [GeForce3 Ti 200] (rev a3)

Is their a way to forcibly reset the sound card?


Rob

---

### Post by kostkon on 2008-08-01
If you mean Flash videos, then install the *libflashsupport* package and you should be fine. But beware, *Firefox* may crash sometimes when visiting pages that contain Flash after doing this.

---

### Post by RheaHS on 2008-08-02
I'm having the same problem, but the solution hasn't worked. 
Also, is there any way to stop the crashing caused by this plugin?

---

### Post by VitaLiNux on 2008-08-02
You should try changing from ALSA to PulseAudio or viceversa. That just works most of the time for me!

---

### Post by RheaHS on 2008-08-02
The only architecture I can get ANY sound to come up on is OSS, but then it doesn't work in firefox. I'm about ready to throw my computer across the room right now, as I now have two without any sound and different problems. What gets me is that this one worked only yesterday

---

