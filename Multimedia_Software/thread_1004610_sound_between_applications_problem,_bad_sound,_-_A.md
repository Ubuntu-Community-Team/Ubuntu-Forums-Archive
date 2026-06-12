---
title: "sound between applications problem, bad sound, - Alsa , OSS , Pulse audio . ."
date: 2008-12-07
forum: Multimedia Software
---

### Post by Linux4theWin on 2008-12-07
Hello there.
I have got me a Toshiba Satellite M70 144
supported audio format : 16-bit stereo
speakers : built-in Harman Kardon stereo speakers
manufacturer : Toshiba Bass Enhanced Sound System with SRS TruSurround XT™ System 

I have been heaving big trouble with my sound lately in Ubuntu. 
Well it all started when i listened to some prodigy songs and suddenly I wanted to become a DJ.
I got me some dj programs that wanted me to install pulse audio for example. 
Well after that my sound went bad . . i uninstall pulse audio but i am still heaving problems. 

*Movie player makes a scratchy sound before playing evry song. 
*I can only listen to music when you tube is closed and the same i can only listen to you tube when music application is closed.
*My sound is not good.  It gets unclear if i turn up the volium just a little. 
*I have tried all the things i have found on the internet in treads related to this matter.
*I cant figure out what driver i should be using and how to uninstall the old one . .or if i should even do that ? , , :S 

I am thinking about turning back to windows but i have just started to love Ubuntu so i am trying to do everything i can before turning back . . . 
If there are some other terminal "Information commands" that might help please post them here and i will post the results.  

Here are some useful information I hope. 
I will very glad if you could help me on this matter.  

  - Greetings ,  
Bjarni

[IMG]http://i36.tinypic.com/14j29s6.png[/IMG]

[IMG]http://i35.tinypic.com/346qekj.png[/IMG]


**Terminal commands ---> : ** 

[quote="aplay -l in terminal gives me "]
**** List of PLAYBACK Hardware Devices ****
card 0: ICH6 [Intel ICH6], device 0: Intel ICH [Intel ICH6]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: ICH6 [Intel ICH6], device 4: Intel ICH - IEC958 [Intel ICH6 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
[/quote]

**_______________________________________________________________________________________________**


[quote="lspci -v in terminal gives me "]
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
	Subsystem: Toshiba America Info Systems Unknown device ff00
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation Mobile 915GM/PM Express PCI Express Root Port (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 00003000-00003fff
	Memory behind bridge: b8100000-b81fffff
	Prefetchable memory behind bridge: c8000000-cfffffff
	Capabilities: <access denied>

00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 00004000-00004fff
	Memory behind bridge: bc000000-bfffffff
	Prefetchable memory behind bridge: 00000000d0000000-00000000d3ffffff
	Capabilities: <access denied>

00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	I/O behind bridge: 00005000-00005fff
	Memory behind bridge: c0000000-c3ffffff
	Prefetchable memory behind bridge: 00000000d4000000-00000000d7ffffff
	Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Toshiba America Info Systems Unknown device ff00
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 1800 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Toshiba America Info Systems Unknown device ff00
	Flags: bus master, medium devsel, latency 0, IRQ 20
	I/O ports at 1820 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Toshiba America Info Systems Unknown device ff00
	Flags: bus master, medium devsel, latency 0, IRQ 21
	I/O ports at 1840 [size=32]

00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Toshiba America Info Systems Unknown device ff00
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at 1860 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03) (prog-if 20 [EHCI])
	Subsystem: Toshiba America Info Systems Unknown device ff00
	Flags: bus master, medium devsel, latency 0, IRQ 19
	Memory at b8000000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3) (prog-if 01 [Subtractive decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=06, subordinate=0a, sec-latency=216
	I/O behind bridge: 00006000-00006fff
	Memory behind bridge: c4000000-c40fffff
	Capabilities: <access denied>

00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
	Subsystem: Toshiba America Info Systems Unknown device ff00
	Flags: bus master, medium devsel, latency 0, IRQ 17
	I/O ports at 1c00 [size=256]
	I/O ports at 1880 [size=64]
	Memory at b8000800 (32-bit, non-prefetchable) [size=512]
	Memory at b8000400 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03) (prog-if 00 [Generic])
	Subsystem: Toshiba America Info Systems Unknown device 0001
	Flags: medium devsel, IRQ 18
	I/O ports at 2400 [size=256]
	I/O ports at 2000 [size=128]
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
	Subsystem: Toshiba America Info Systems Unknown device ff00
	Flags: bus master, medium devsel, latency 0

00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03) (prog-if 8a [Master SecP PriP])
	Subsystem: Toshiba America Info Systems Unknown device ff00
	Flags: bus master, medium devsel, latency 0, IRQ 21
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at 18c0 [size=16]

00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 03) (prog-if 8f [Master SecP SecO PriP PriO])
	Subsystem: Toshiba America Info Systems Unknown device ff00
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 20
	I/O ports at 2088 [size=8]
	I/O ports at 18ec [size=4]
	I/O ports at 2080 [size=8]
	I/O ports at 18e8 [size=4]
	I/O ports at 18f0 [size=16]
	Memory at b8000c00 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>

00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
	Subsystem: Toshiba America Info Systems Unknown device ff00
	Flags: medium devsel, IRQ 11
	I/O ports at 20a0 [size=32]

01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility X700 (PCIE) (prog-if 00 [VGA controller])
	Subsystem: Toshiba America Info Systems Unknown device ff02
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at c8000000 (32-bit, prefetchable) [size=128M]
	I/O ports at 3000 [size=256]
	Memory at b8100000 (32-bit, non-prefetchable) [size=64K]
	[virtual] Expansion ROM at b8120000 [disabled] [size=128K]
	Capabilities: <access denied>

06:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
	Subsystem: Toshiba America Info Systems Unknown device ff00
	Flags: bus master, medium devsel, latency 32, IRQ 22
	I/O ports at 6000 [size=256]
	Memory at c4006000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

06:04.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
	Subsystem: Toshiba America Info Systems Unknown device ff00
	Flags: bus master, medium devsel, latency 168, IRQ 16
	Memory at c4007000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=06, secondary=07, subordinate=0a, sec-latency=176
	Memory window 0: 88000000-8bfff000 (prefetchable)
	Memory window 1: 8c000000-8ffff000
	I/O window 0: 00006400-000064ff
	I/O window 1: 00006800-000068ff
	16-bit legacy interface ports at 0001

06:04.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller (prog-if 10 [OHCI])
	Subsystem: Toshiba America Info Systems Unknown device ff00
	Flags: bus master, medium devsel, latency 32, IRQ 21
	Memory at c4006800 (32-bit, non-prefetchable) [size=2K]
	Memory at c4000000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

06:04.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
	Subsystem: Toshiba America Info Systems Unknown device ff05
	Flags: bus master, medium devsel, latency 57, IRQ 17
	Memory at c4004000 (32-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>

06:04.4 SD Host controller: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller
	Subsystem: Toshiba America Info Systems Unknown device ff05
	Flags: bus master, medium devsel, latency 57, IRQ 20
	Memory at c4008400 (32-bit, non-prefetchable) [size=256]
	Memory at c4008000 (32-bit, non-prefetchable) [size=256]
	Memory at c4006400 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

07:00.0 Network controller: RaLink Unknown device 0601
	Subsystem: Belkin Unknown device 8013
	Flags: bus master, slow devsel, latency 64, IRQ 16
	Memory at 8c000000 (32-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>

[/quote]

---

### Post by unutbu on 2008-12-07
You might want to try 
```

sudo apt-get --simulate purge linux-sound-base
```
This will simulate the removal of the linux-sound-base package and all packages that depend on it. It will not actually remove any packages.

On my system the output looks like this:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  alsa-base* alsa-utils* fast-user-switch-applet* gdm* gdm-guest-session*
  linux-sound-base* ubuntu-desktop*
0 upgraded, 0 newly installed, 7 to remove and 146 not upgraded.
Purg ubuntu-desktop [1.124]
Purg alsa-base [1.0.17.dfsg-2ubuntu1]
Purg gdm-guest-session [0.6]
Purg fast-user-switch-applet [2.24.0-0ubuntu6]
Purg gdm [2.20.8-0ubuntu3]
Purg alsa-utils [1.0.17-0ubuntu2]
Purg linux-sound-base [1.0.17.dfsg-2ubuntu1]
```

By purging these packages you will hopefully remove any messed up configuration files. Then you can reinstall these packages and your sound configurations should be like when you first installed Ubuntu.

So, if you wish to try it for real, type
```

sudo apt-get purge linux-sound-base
sudo apt-get install linux-sound-base alsa-utils alsa-base gdm fast-user-switch-apple gdm-guest-session ubuntu-desktop
```

This idea comes from LordRaiden's 
"Comprehensive Sound Problem Solutions Guide v0.5e"
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---

### Post by Linux4theWin on 2008-12-07
> **unutbu said:**
> You might want to try 
```

sudo apt-get --simulate purge linux-sound-base
```
This will simulate the removal of the linux-sound-base package and all packages that depend on it. It will not actually remove any packages.

On my system the output looks like this:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  alsa-base* alsa-utils* fast-user-switch-applet* gdm* gdm-guest-session*
  linux-sound-base* ubuntu-desktop*
0 upgraded, 0 newly installed, 7 to remove and 146 not upgraded.
Purg ubuntu-desktop [1.124]
Purg alsa-base [1.0.17.dfsg-2ubuntu1]
Purg gdm-guest-session [0.6]
Purg fast-user-switch-applet [2.24.0-0ubuntu6]
Purg gdm [2.20.8-0ubuntu3]
Purg alsa-utils [1.0.17-0ubuntu2]
Purg linux-sound-base [1.0.17.dfsg-2ubuntu1]
```

By purging these packages you will hopefully remove any messed up configuration files. Then you can reinstall these packages and your sound configurations should be like when you first installed Ubuntu.

So, if you wish to try it for real, type
```

sudo apt-get purge linux-sound-base
sudo apt-get install linux-sound-base alsa-utils alsa-base gdm fast-user-switch-apple gdm-guest-session ubuntu-desktop
```

This idea comes from LordRaiden's 
"Comprehensive Sound Problem Solutions Guide v0.5e"
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

Tanks for posting this.  
i tryed it and it did not work and i got some error in the end. 
After that my computer battery went emty and my laptop turned off without a normal shutdown.
after that i cannot boot into linux anymore and i get the 
"
Kinit: name_to_dev_t(/dev/disk/something . .
kinit: No resume image, doing normal boot...
"
I dont have time for this problem right now , it seems very complicated to fix, so i will join bill gates team for a wile.

Thank you. 
Greetings ,  
Bjarni

---

