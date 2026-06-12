---
title: "Internal/External Mic Not Working"
date: 2010-05-04
forum: Multimedia Software
---

### Post by teamcoltra on 2010-05-04
SOLUTION FIRST:
> **lidex said:**
> OK. Update your kernel:
```
sudo apt-get update
sudo apt-get upgrade
```
Now reboot so we can work with the latest kernel.
Install alsa backports:
```
sudo apt-get install linux-backports-modules-alsa-lucid-generic
``` Reboot again.

Check your levels in alsamixer.
```
 alsamixer 
```
Press F6 to select the correct soundcard.
Press F3 to show playback levels. F4 selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.

Also try gnome-alsamixer and make sure to enable everything in 'Edit>Soundcard Properties'

**HERE WAS MY PROBLEM:**

Ever since I switched from windows I have not been able to get my internal or external mic to work, I was hoping that this would be fixed upon upgrade, but it has not been. So I am posting here so maybe someone can help me skype with my family when I move back to Alaska. 

**Here is the LSPCI for my soundcard:** 
> 01:05.1 Audio device: ATI Technologies Inc RS780 Azalia controller
	Subsystem: Acer Incorporated [ALI] Device 021a
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 32 bytes
	Interrupt: pin B routed to IRQ 28
	Region 0: Memory at cfdec000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 3
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [a0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+
		Address: 00000000fee0300c  Data: 4191
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel


*I have also checked the alsamixer and it shows the volume is turned all the way up for both internal and external... and they are not muted. *

Hopefully you guys can help me figure this out.

[COLOR="White"]Tags: Ubuntu, Gateway, NV5214u, 9.10, Pulse, No Mic, Fixed, ALSA, Lucid, Internal, External, Microphone[/COLOR]

---

### Post by teamcoltra on 2010-05-05
Is there more information I could provide to make helping me easier?

---

### Post by lidex on 2010-05-06
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#*
```
Terminal="Applications->Accessories->Terminal"
Please post text output using code tags. Also helpful is the make/model of your PC/Laptop.

---

### Post by teamcoltra on 2010-05-06
teamcoltra@paradoxicon:~$ uname -a
Linux paradoxicon 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:09:38 UTC 2010 x86_64 GNU/Linux
teamcoltra@paradoxicon:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
teamcoltra@paradoxicon:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.23.
Compiled on May  4 2010 for kernel 2.6.32-21-generic (SMP).
teamcoltra@paradoxicon:~$ head -n 1 /proc/asound/card*/codec#*
==> /proc/asound/card0/codec#0 <==
Codec: Conexant CX20561 (Hermosa)

==> /proc/asound/card0/codec#1 <==
Codec: Conexant ID 2c06

==> /proc/asound/card1/codec#0 <==
Codec: ATI RS690/780 HDMI
teamcoltra@paradoxicon:~$

---

### Post by lidex on 2010-05-06
What is the make/model of this PC?

---

### Post by teamcoltra on 2010-05-07
NV5214u Gateway

---

### Post by lidex on 2010-05-08
OK. Update your kernel:
```
sudo apt-get update
sudo apt-get upgrade
```
Now reboot so we can work with the latest kernel.
Install alsa backports:
```
sudo apt-get install linux-backports-modules-alsa-lucid-generic
``` Reboot again.

Check your levels in alsamixer.
```
 alsamixer 
```
Press F6 to select the correct soundcard.
Press F3 to show playback levels. F4 selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.

Also try gnome-alsamixer and make sure to enable everything in 'Edit>Soundcard Properties'

---

### Post by teamcoltra on 2010-05-10
Thank you, fixed, and updated main post with your solution, and some tags to help people with similar issues find this page.

---

### Post by tuxar on 2010-05-11
Thanks, this works also with
tuxar@tuxlap:~$ uname -a
Linux tuxlap 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:27:30 UTC 2010 i686 GNU/Linux
tuxar@tuxlap:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC260 Analog [ALC260 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC260 Digital [ALC260 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
tuxar@tuxlap:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.22.1.
Compiled on Apr 29 2010 for kernel 2.6.32-22-generic (SMP).
tuxar@tuxlap:~$ head -n 1 /proc/asound/card*/codec#*
==> /proc/asound/card0/codec#0 <==
Codec: Realtek ALC260

==> /proc/asound/card0/codec#1 <==
Codec: LSI ID 1040

---

