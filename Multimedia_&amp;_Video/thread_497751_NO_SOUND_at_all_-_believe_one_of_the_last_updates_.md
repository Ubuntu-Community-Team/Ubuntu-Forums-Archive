---
title: "NO SOUND at all - believe one of the last updates is bugged"
date: 2007-07-10
forum: Multimedia &amp; Video
---

### Post by kopolov on 2007-07-10
Hi,
Today I reinstalled Ubuntu 7.04.
At first, sound worked fine.
After I installed all the updates (through the update manger), sound stopped completely, even though the sound card is recognized OK.

The reason I reinstalled it was because the sound went dead the first time, and after I tried several suggestions (the last one included reinstalling the alsa package), I also lost GUI (and since I am quite a NB, I did not know what to do except for reinstalling UBUNTU)

Hardware details:
IBM thinkpad T23. PIII 1000MHZ cpu.
 sound card - intel 82801CA-ICH3

aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: I82801CAICH3 [Intel 82801CA-ICH3], device 0: Intel ICH [Intel 82801CA-ICH3]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

lspci -v
00:00.0 Host bridge: Intel Corporation 82830 830 Chipset Host Bridge (rev 04)
        Subsystem: IBM ThinkPad A/T/X Series
        Flags: bus master, fast devsel, latency 0
        Memory at d0000000 (32-bit, prefetchable) [size=256M]
        Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation 82830 830 Chipset AGP Bridge (rev 04) (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, fast devsel, latency 96
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
        Memory behind bridge: c0100000-c01fffff
        Prefetchable memory behind bridge: e0000000-ebffffff

00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB (Hub #1) (rev 02) (prog-if 00 [UHCI])
        Subsystem: IBM ThinkPad A/T/X Series
        Flags: bus master, medium devsel, latency 0, IRQ 11
        I/O ports at 1800 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801CA/CAM USB (Hub #2) (rev 02) (prog-if 00 [UHCI])
        Subsystem: IBM ThinkPad A/T/X Series
        Flags: bus master, medium devsel, latency 0, IRQ 11
        I/O ports at 1820 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801CA/CAM USB (Hub #3) (rev 02) (prog-if 00 [UHCI])
        Subsystem: IBM ThinkPad A/T/X Series
        Flags: bus master, medium devsel, latency 0, IRQ 11
        I/O ports at 1840 [size=32]

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 42) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=08, sec-latency=64
        I/O behind bridge: 00002000-00006fff
        Memory behind bridge: c0200000-cfffffff
        Prefetchable memory behind bridge: f0000000-f7ffffff

00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 02)
        Flags: bus master, medium devsel, latency 0

00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 (rev 02) (prog-if 8a [Master SecP PriP])
        Subsystem: IBM ThinkPad A/T/X Series
        Flags: bus master, medium devsel, latency 0, IRQ 11
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at 1860 [size=16]
        Memory at 50001000 (32-bit, non-prefetchable) [size=1K]

00:1f.3 SMBus: Intel Corporation 82801CA/CAM SMBus Controller (rev 02)
        Subsystem: IBM ThinkPad A/T/X Series
        Flags: medium devsel, IRQ 11
        I/O ports at 1880 [size=32]

00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 02)
        Subsystem: IBM ThinkPad T23 (2647-4MG) or A30/A30p (2652/2653)
        Flags: bus master, medium devsel, latency 0, IRQ 11
        I/O ports at 1c00 [size=256]
        I/O ports at 18c0 [size=64]

01:00.0 VGA compatible controller: S3 Inc. SuperSavage IX/C SDR (rev 05) (prog-if 00 [VGA])
        Subsystem: IBM ThinkPad T23 (2647-4MG)
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 11
        Memory at c0100000 (32-bit, non-prefetchable) [size=512K]
        Memory at e8000000 (32-bit, prefetchable) [size=64M]
        Memory at e4000000 (32-bit, prefetchable) [size=64M]
        Memory at e0000000 (32-bit, prefetchable) [size=32M]
        [virtual] Expansion ROM at e2000000 [disabled] [size=64K]
        Capabilities: <access denied>

02:00.0 CardBus bridge: Texas Instruments PCI1420
        Subsystem: IBM ThinkPad T23 (2647-4MG)
        Flags: bus master, medium devsel, latency 168, IRQ 11
        Memory at 50000000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=02, secondary=03, subordinate=06, sec-latency=176
        Memory window 0: f0000000-f3fff000 (prefetchable)
        Memory window 1: c4000000-c7fff000
        I/O window 0: 00002000-000020ff
        I/O window 1: 00002400-000024ff
        16-bit legacy interface ports at 0001

02:00.1 CardBus bridge: Texas Instruments PCI1420
        Subsystem: IBM ThinkPad T23 (2647-4MG)
        Flags: bus master, medium devsel, latency 168, IRQ 11
        Memory at 51000000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=02, secondary=07, subordinate=07, sec-latency=176
        Memory window 0: f4000000-f7fff000 (prefetchable)
        Memory window 1: c8000000-cbfff000
        I/O window 0: 00002800-000028ff
        I/O window 1: 00002c00-00002cff
        16-bit legacy interface ports at 0001

02:02.0 Communication controller: Agere Systems WinModem 56k (rev 01)
        Subsystem: AMBIT Microsystem Corp. IBM ThinkPad T23 (2647-4MG)
        Flags: bus master, medium devsel, latency 0, IRQ 11
        Memory at c0201000 (32-bit, non-prefetchable) [size=256]
        I/O ports at 6440 [size=8]
        I/O ports at 6000 [size=256]
        Capabilities: <access denied>

02:08.0 Ethernet controller: Intel Corporation 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller (rev 42)
        Subsystem: IBM ThinkPad A/T/X Series
        Flags: bus master, medium devsel, latency 66, IRQ 11
        Memory at c0200000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at 6400 [size=64]
        Capabilities: <access denied>

I am a NB in linux (so please, be very clear with your suggestions).
Thanks,

Hagai

---

### Post by kopolov on 2007-07-12
Anyone??????
I NEED HELP (beside mental help)
PLEASE :)

---

### Post by acaby on 2007-07-18
I have Ubuntu 7.04 and my sound worked perfectly UNTIL I installed the updates from the update manager. (about 180mb) 
EXACTLY the same problem you are having.

Try this fix:

Getting the ALSA drivers from a *fresh* kernel

Sometimes, sound might be configured correctly, but for some reason or another (tinkering) it stops working. One way to go back to the old setup is to reinstall Ubuntu. However, this step is actually quite unnecessary since you are reinstalling everything because of one thing.

I did this and my sound came back after reboot. I think  there must have been a bug in one of the update files.
In case the below fix will not work for you, however it should, You can find the Complete solution from this post:
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)
You may want to look at it just in case you see a solution that may work for you other than the one I have suggested below

[COLOR="Red"]**A faster way, is to just remove the problematic packages and reinstall them cleanly.**[/COLOR] 

(1) Remove these packages
Code:

sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils


(2) Reinstall those same packages
Code:

sudo apt-get install linux-sound-base alsa-base alsa-utils

VERY IMPORTANT NOTE: Ubuntu (GNOME) users have reported that packages 'gdm' and 'ubuntu-desktop' are removed after removing the linux-sound-base packages. If this happens, then do the following
Code:

sudo apt-get install gdm ubuntu-desktop


(3) Reboot

VERY IMPORTANT NOTE: Xubuntu (XFCE) users have reported that packages 'gdm' and 'xubuntu-desktop' are removed after removing the linux-sound-base packages. If this happens, then do the following
Code:

sudo apt-get install gdm xubuntu-desktop


(3) Reboot


Hope this helps
Good Luck,
Arthur

---

### Post by kopolov on 2007-07-30
OK,
I did the following and it succeeded, but I am not sure why:
1. I used pqmagic to completely remove all data from my harddrive
2. Reinstalled UBUNTU 7.04 (from the live CD)
3. When I was required to update, I deselected all updates regarding the linux kernel (meaning, all updates which starts with linux)
4. After finishing the update (previous section), I selected the above mentioned linux kernel updates and finished the update processed.
This time the sound did not disappear.

I hope it will help.

Hagai

---

### Post by Deeman on 2007-08-03
All due respect...  Both of these fixes don't really work.  The first is a great shot at fixing the bug and I hope for an expansion on this fix but the second is kind of unproductive.  Reinstall the OS?  If I wanted to use a fix like that then I would have kept using Windows????  LOL

:lolflag:

---

### Post by kopolov on 2007-09-25
Deemon,
I was **very** new to ubuntu when I wrote that. It was the only thing I had in mind.
Today I (hopefully) a little smarter (apt-get, synaptic, etc ...)

---

### Post by keeper-of-the-real on 2007-09-25
Just wanted to add that I have the same sound card and exact same problem.  Returned my sound using ALSA.

---

### Post by lank23 on 2007-10-09
I have the same T-23 with the same sound card with 7.04 with all the updates and my sound has never had and issue during any of the update processes over the last 6 or so months of using 7.04.

lank23

---

### Post by fbn on 2007-10-23
Hi,

I also have this issue - with Ubuntu 7.04 and Ubuntu 7.10

Is there any fix for this?

Frank

---

### Post by lank23 on 2007-10-23
Is the correct module loading for you sound card?

---

### Post by fbn on 2007-10-24
Yes I think so. aplay -l shows the soundcard and the sound mixer also shows the soundcard. I am able to adjust the volume with alsamixer but there is still no sound ...

---

### Post by lank23 on 2007-10-24
do you get sound from the headphone jack?

---

