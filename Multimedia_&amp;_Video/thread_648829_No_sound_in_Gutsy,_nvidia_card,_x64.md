---
title: "No sound in Gutsy, nvidia card, x64"
date: 2007-12-24
forum: Multimedia &amp; Video
---

### Post by TheSwaz on 2007-12-24
To start, I have tried everything that I have googled and everything that i found in this forum, but to no avail.

Here is what is happening:
I installed Gutsy a month or so ago.  After getting nvidia video drivers and wireless to work, everything else worked perfectly, including sound.  Fast forward to about a week ago, and my sound randomly stopped working.  The only things that I believe I had changed were themes.  Sound will not work in any program, and will not give me a log in or off sound, or anything.  However, when I boot up Windows, sound works just fine, so it is not disabled in BIOS (not that it would even matter for me since I have a ****-tacular phoenix BIOS that won't let me change anything in the first place).

What I have tried:
Everything and anything I have found in these forums, along with a couple others and nothing seems to work.  I updated alsa, turned all volumes up in alsa-mixer, looked entirely through gconf-editor and made sure everything was enabled there, along with a few other things, like editing asound.state, updating from all repositories, and still nothing.  It doesn't seem that I have any unusual messages in my system log, but then again I don't know exactly where to look.  One thing that I did notice is that my sound card is interrupt 21, and in messages it gives me stuff like 
Dec 24 01:21:54 swaz-laptop kernel: [   12.402272] ACPI: PCI Interrupt Link [LSMB] (IRQs 20 21 22) *0

My setup:
HP pavilion laptop, nvidia nforce3 on board sound card, Ubuntu 7.10 x64
lspci gives me:
00:00.0 Host bridge: nVidia Corporation nForce3 Host Bridge (rev a4)
00:01.0 ISA bridge: nVidia Corporation nForce3 LPC Bridge (rev a6)
00:01.1 SMBus: nVidia Corporation nForce3 SMBus (rev a4)
00:02.0 USB Controller: nVidia Corporation nForce3 USB 1.1 (rev a5)
00:02.1 USB Controller: nVidia Corporation nForce3 USB 1.1 (rev a5)
00:02.2 USB Controller: nVidia Corporation nForce3 USB 2.0 (rev a2)
00:06.0 Multimedia audio controller: nVidia Corporation nForce3 Audio (rev a2)
00:06.1 Modem: nVidia Corporation nForce3 Audio (rev a2)
00:08.0 IDE interface: nVidia Corporation nForce3 IDE (rev a5)
00:0a.0 PCI bridge: nVidia Corporation nForce3 PCI Bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation nForce3 AGP Bridge (rev a4)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 440 Go 64M] (rev a3)
02:00.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
02:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:02.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
02:04.0 CardBus bridge: Texas Instruments PCI1620 PC Card Controller (rev 01)
02:04.1 CardBus bridge: Texas Instruments PCI1620 PC Card Controller (rev 01)
02:04.2 System peripheral: Texas Instruments PCI1620 Firmware Loading Function (rev 01)


If any other information would be helpful, please let me know.  I am leaving town tomorrow morning, but will be back to check on Wednesday.  

Please PLEASE....if you have any idea what is going on here, help me out.  I hate reverting back to Windows after I have been using this wonderful OS.

-Swaz

---

### Post by TheSwaz on 2007-12-24
bump.

sorry, i really want to get this figured out, and literally *nothing* has worked yet

---

### Post by TheSwaz on 2007-12-27
aHA.  Followed Temujin's insturctions for OSS, sound working great now.  Thanks a ton Temujin!

---

### Post by Yellow Pasque on 2007-12-27
> **TheSwaz said:**
> Thanks a ton Temujin! No problem. Glad it worked.

---

