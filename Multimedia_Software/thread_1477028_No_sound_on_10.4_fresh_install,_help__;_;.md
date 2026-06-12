---
title: "No sound on 10.4 fresh install, help  ; ;"
date: 2010-05-08
forum: Multimedia Software
---

### Post by Blindsushi on 2010-05-08
I just installed the latest version, updated it and everything, but I can't get my sound to work.
I have an onboard sound card, and a Soundblaster too.

Here are the lspci results:
> 
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:01.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to AGP Controller (rev 02)
00:06.0 System peripheral: Intel Corporation 82865G/PE/P Processor to I/O Memory Interface (rev 02)
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
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AQ [Radeon 9600]
01:00.1 Display controller: ATI Technologies Inc RV350 AQ [Radeon 9600] (Secondary)
02:05.0 Ethernet controller: SysKonnect SK-9871 V2.0 Gigabit Ethernet 1000Base-ZX Adapter, PCI64, Fiber ZX/SC (rev 10)
02:0a.0 Multimedia audio controller: Creative Labs CA0106 Soundblaster
02:0d.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)


And the aplay -l results:
> 
**** List of PLAYBACK Hardware Devices ****
card 0: ICH5 [Intel ICH5], device 0: Intel ICH [Intel ICH5]
Subdevices: 1/1
Subdevice #0: subdevice #0
card 0: ICH5 [Intel ICH5], device 4: Intel ICH - IEC958 [Intel ICH5 - IEC958]
Subdevices: 1/1
Subdevice #0: subdevice #0
card 1: CA0106 [CA0106], device 0: ca0106 [CA0106]
Subdevices: 1/1
Subdevice #0: subdevice #0
card 1: CA0106 [CA0106], device 1: ca0106 [CA0106]
Subdevices: 1/1
Subdevice #0: subdevice #0
card 1: CA0106 [CA0106], device 2: ca0106 [CA0106]
Subdevices: 1/1
Subdevice #0: subdevice #0
card 1: CA0106 [CA0106], device 3: ca0106 [CA0106]
Subdevices: 1/1
Subdevice #0: subdevice #0


Then I have no clue what to do : (
I'd like to be able to get my Soundblaster to work, cause I plan on dual booting with WinXp, but if the only way is the onboard way, I'm cool with it.

---

### Post by Blindsushi on 2010-05-08
Anybody?

---

### Post by ikester8 on 2010-05-08
The same thing happened to me. It's silly, but on the initial upgrade, the sound is muted. Go to System|Preferences|Sound. Make sure Mute isn't checked on the Output Volume.

---

### Post by lidex on 2010-05-08
Have you tried disabling onboard audio in bios?

---

### Post by etherealknight on 2010-05-08
I have the same problem on my hp pavillion  dv6119us I've tried so many different things, but only the headphones give any output... I have a conexant sound card with the venice chip. Ubuntu is using the hda driver and the snd-hda-intel module. I once had sound back in jaunty with a fresh install, but that was ages ago....

---

### Post by lidex on 2010-05-08
> **etherealknight said:**
> I have the same problem on my hp pavillion  dv6119us I've tried so many different things, but only the headphones give any output... I have a conexant sound card with the venice chip. Ubuntu is using the hda driver and the snd-hda-intel module. I once had sound back in jaunty with a fresh install, but that was ages ago....

Let's not divert the thread. Start a new one and PM me the link.

---

