---
title: "Problems with sound"
date: 2008-01-12
forum: Multimedia &amp; Video
---

### Post by PacoCrespo on 2008-01-12
Hello, I get very low quality when I play music or video in my pc, I don't know what to do, any sugest,

---

### Post by balaknair on 2008-01-12
Hi PacoCrespo
If you mention your system specs and a few other details it'll be easier to help

Open a terminal and type in 
aplay -l
lspci -v

and post the text output you get here.
It'll help others to understand the problem better and solve it.

You can also take a look at the comprehensive sound problem solutions guide at [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---

### Post by PacoCrespo on 2008-01-12
Hi, this is what I get:

00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub (rev 0e)
        Subsystem: Hewlett-Packard Company Unknown device 2a28
        Flags: bus master, fast devsel, latency 0
        Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL PCI Express Root Port (rev 0e) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        Memory behind bridge: fa900000-fe9fffff
        Prefetchable memory behind bridge: bff00000-dfefffff
        Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 05)
        Subsystem: Hewlett-Packard Company Unknown device 2a28
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at febfc000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 05) (prog-if 00 [UHCI])
        Subsystem: Hewlett-Packard Company Unknown device 2a28
        Flags: bus master, medium devsel, latency 0, IRQ 17
        I/O ports at ec00 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 05) (prog-if 00 [UHCI])
        Subsystem: Hewlett-Packard Company Unknown device 2a28
        Flags: bus master, medium devsel, latency 0, IRQ 18
        I/O ports at e880 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 05) (prog-if 00 [UHCI])
        Subsystem: Hewlett-Packard Company Unknown device 2a28
        Flags: bus master, medium devsel, latency 0, IRQ 19
        I/O ports at e800 [size=32]

00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 05) (prog-if 00 [UHCI])
        Subsystem: Hewlett-Packard Company Unknown device 2a28
        Flags: bus master, medium devsel, latency 0, IRQ 16
        I/O ports at e480 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 05) (prog-if 20 [EHCI])
        Subsystem: Hewlett-Packard Company Unknown device 2a28
        Flags: bus master, medium devsel, latency 0, IRQ 17
        Memory at febfbc00 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d5) (prog-if 01 [Subtractive decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=32
        I/O behind bridge: 0000d000-0000dfff
        Memory behind bridge: fea00000-feafffff
        Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 05)
        Subsystem: Hewlett-Packard Company Unknown device 2a28
        Flags: bus master, medium devsel, latency 0

00:1f.2 IDE interface: Intel Corporation 82801FB/FW (ICH6/ICH6W) SATA Controller (rev 05) (prog-if 80 [Master])
        Subsystem: Hewlett-Packard Company Unknown device 2a28
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 18
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at ffa0 [size=16]
        Capabilities: <access denied>

00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 05)
        Subsystem: Hewlett-Packard Company Unknown device 2a28
        Flags: medium devsel, IRQ 10
        I/O ports at 0400 [size=32]

01:00.0 VGA compatible controller: nVidia Corporation NV44 [GeForce 6200 SE TurboCache (TM)] (rev a1) (prog-if 00 [VGA])
        Subsystem: ASUSTeK Computer Inc. Unknown device 0345
        Flags: bus master, fast devsel, latency 0, IRQ 10
        Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
        Memory at c0000000 (64-bit, prefetchable) [size=256M]
        Memory at fc000000 (64-bit, non-prefetchable) [size=16M]
        Expansion ROM at fe9e0000 [disabled] [size=128K]
        Capabilities: <access denied>

02:08.0 Ethernet controller: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller (rev 05)
        Subsystem: Hewlett-Packard Company Unknown device 2a28
        Flags: bus master, medium devsel, latency 64, IRQ 20
        Memory at feaff000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at dc00 [size=64]
        Capabilities: <access denied>

02:09.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80) (prog-if 10 [OHCI])
        Subsystem: Hewlett-Packard Company Unknown device 2a28
        Flags: bus master, medium devsel, latency 64, IRQ 21
        Memory at feafe800 (32-bit, non-prefetchable) [size=2K]
        I/O ports at d880 [size=128]
        Capabilities: <access denied>

thanks a lot¡¡¡

---

### Post by PacoCrespo on 2008-01-12
Excuse me I did not include this part

**** Lista de PLAYBACK Dispositivos Hardware ****
tarjeta 0: Intel [HDA Intel], dispositivo 0: ALC880 Analog [ALC880 Analog]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0
tarjeta 0: Intel [HDA Intel], dispositivo 1: ALC880 Digital [ALC880 Digital]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0


Thanks again

---

### Post by balaknair on 2008-01-12
Sorry for the delay in replying
That last bit was what we needed to identify your sound card

Now type this command(or copy paste) in a terminal
```
cat /proc/asound/card0/codec#* | grep Codec
```
This will tell you what codec your card uses
I think it should be ALC880

now go to this page [http://www.mjmwired.net/kernel/Documentation/sound/alsa/ALSA-Configuration.txt](http://www.mjmwired.net/kernel/Documentation/sound/alsa/ALSA-Configuration.txt)

Find the codec your card uses, and check the model descriptions to find which one matches your sound system the best.
for ALC880:
```
ALC880
783		  3stack	3-jack in back and a headphone out
784		  3stack-digout	3-jack in back, a HP out and a SPDIF out
785		  5stack	5-jack in back, 2-jack in front
786		  5stack-digout	5-jack in back, 2-jack in front, a SPDIF out
787		  6stack	6-jack in back, 2-jack in front
788		  6stack-digout	6-jack with a SPDIF out
789		  w810		3-jack
790		  z71v		3-jack (HP shared SPDIF)
791		  asus		3-jack (ASUS Mobo)
792		  asus-w1v	ASUS W1V
793		  asus-dig	ASUS with SPDIF out
794		  asus-dig2	ASUS with SPDIF out (using GPIO2)
795		  uniwill	3-jack
796		  fujitsu	Fujitsu Laptops (Pi1536)
797		  F1734		2-jack
798		  lg		LG laptop (m1 express dual)
799		  lg-lw		LG LW20/LW25 laptop
800		  tcl		TCL S700
801		  clevo		Clevo laptops (m520G, m665n)
802		  test		for testing/debugging purpose, almost all controls can be
803				adjusted.  Appearing only when compiled with
804				$CONFIG_SND_DEBUG=y
805		  auto		auto-config reading BIOS (default)
```

Now back to the terminal
```
sudo nano /etc/modprobe.d/alsa-base
```
Navigate to the end of the file(use down arrow key to scroll down all the way) and paste this line as the last line
```
options snd-hda-intel model=MODEL
```
where MODEL is replaced with the model from the above lines which matches your setup.
eg: if your PC is an LG LW20  laptop select lg-lw so that the line reads
options snd-hda-intel model=lg-lw

save and exit

Reboot

Hope this helps. This is based on this excellent guide here [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto).
Another useful guide for sound problems is [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)
Please be sure to reply and let me know how it goes, and if it fixes your sound, please mark the thread as solved.
All the best

---

