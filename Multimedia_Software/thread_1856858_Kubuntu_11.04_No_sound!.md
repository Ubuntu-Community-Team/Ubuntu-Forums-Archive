---
title: "Kubuntu 11.04 No sound!"
date: 2011-10-09
forum: Multimedia Software
---

### Post by khaos1 on 2011-10-09
Hi guys. Suddently after a reboot I have no sound in my pc. I have tested that sound card is working ok in Windows XP (dual boot).

I have uninstalled and reinstalled pulseaudio and pavucontrol with no luck. I also reinstalled alsa-utils etc with no luck.

In my pc I have 2 cards. One was disabled and the Soundblaster Audigy that I used. 

I don't know what to do in order to fix that. Do you want to provide an alsa output or something?

aplay -l:
> **** List of PLAYBACK Hardware Devices ****
card 0: CA0106 [CA0106], device 0: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 1: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 2: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 3: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
lspci:
> 00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub (rev 0e)
00:01.0 PCI bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL PCI Express Root Port (rev 0e)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 05)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 05)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 05)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 05)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d5)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 05)
00:1f.2 IDE interface: Intel Corporation 82801FB/FW (ICH6/ICH6W) SATA Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 05)
01:00.0 VGA compatible controller: ATI Technologies Inc R430 [Radeon X800 XL] (PCIe)
01:00.1 Display controller: ATI Technologies Inc R430 [Radeon X800 XL] (PCIe) (Secondary)
**02:01.0 Multimedia audio controller: Creative Labs CA0106 Soundblaster**
02:05.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 13)
02:06.0 RAID bus controller: VIA Technologies, Inc. VT6410 ATA133 RAID controller (rev 06)
I tried to run alsa-info.sh but giving some errors. here is the output: [http://pastie.org/2664833](http://pastie.org/2664833)

I want to purge -remove all sound settings and to reinstall them again but I don't know how. Can you help?

---

### Post by idokus on 2011-11-05
Did you do anything with muting? 

(I closed down with a muted CA0106, and after that it didn't come up again. It shows up, but nothing happens when I unmute or fiddle with the soundlevels of the sound card.)

---

### Post by khaos1 on 2012-01-02
> **idokus said:**
> Did you do anything with muting? 

(I closed down with a muted CA0106, and after that it didn't come up again. It shows up, but nothing happens when I unmute or fiddle with the soundlevels of the sound card.)

Maybe but now what is the fix for that? :/ Do you solved this prob?
Thanks in advance

---

### Post by idokus on 2012-01-03
I made a clean install for Kubuntu 11.10, that fixed my problem.

---

### Post by khaos1 on 2012-01-03
> **idokus said:**
> I made a clean install for Kubuntu 11.10, that fixed my problem.

Haha I have made exactly the same think. But I think that is no a kewl solution :)

---

