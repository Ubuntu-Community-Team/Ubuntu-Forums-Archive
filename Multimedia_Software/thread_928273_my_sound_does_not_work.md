---
title: "my sound does not work"
date: 2008-09-23
forum: Multimedia Software
---

### Post by Static42 on 2008-09-23
My sound does not work on my computer. I have a Creative X-Fi XtremeGamer card installed. I followed the [OSS guide]("https://help.ubuntu.com/community/OpenSound") exactly. My computer does recognize my card, however, so it could just be a driver problem.
When I view the OSS Mixer panel, the bars do flash when I try playing a video in VLC, but I can't hear any sound. My speakers work perfectly in Windows XP, so they should be able to work in Ubuntu. Volume is not muted and is at a decent level. I'm kind of stuck right here.

---

### Post by Crafty Kisses on 2008-09-23
I'd like to see the results of this command:
```
lspci
```

---

### Post by Static42 on 2008-09-23
> 
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IR (ICH9R) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801IR/IO/IH (ICH9R/DO/DH) 4 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801I (ICH9 Family) 2 port SATA IDE Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8600 GT (rev a1)
03:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
03:00.1 IDE interface: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
05:01.0 Multimedia audio controller: Creative Labs SB X-Fi


By the way, I shouldn't have said that there was absolutely no sound. There is sound, but it is so low that I can hardly hear it, even with headphones.

---

### Post by tuxxy on 2008-09-23
Did you try increasing the volume then

---

### Post by Static42 on 2008-09-23
Yes, I have tried increasing the volume, but it's stuck at 57%. It won't go any higher than that. When I try to move the slider up to 100%, it just drops back down to 57%. I am not sure why it's doing that.

---

### Post by Static42 on 2008-09-25
Any suggestions, or should I just buy a new sound card that I know will work with ubuntu?

---

