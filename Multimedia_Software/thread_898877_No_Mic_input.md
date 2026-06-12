---
title: "No Mic input"
date: 2008-08-23
forum: Multimedia Software
---

### Post by Zabadda on 2008-08-23
Im running Ubuntu 8.04 but i cant get my mic to work, its a working mic so i know its ok but i cant get any pick up, ive tried un-muting everything and turning it all up but still nothing.

Zabadda

---

### Post by VictorR on 2008-08-23
I also tried to get microphone working and failed. I have two cards: one is in-built AC'97 and a cheap USB 3D Sound model PD 552.
```
$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: V8237 [VIA 8237], device 0: VIA 8237 [VIA 8237]
  Subdevices: 3/4
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
card 0: V8237 [VIA 8237], device 1: VIA 8237 [VIA 8237]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: default [USB  AUDIO  ], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

and my .asoundrc
```
pcm.USBsound {
    type hw
    card 1
    device 0
}

pcm.softvol {
    type            softvol
    slave {
        pcm         "USBsound"
    }
    control {
        name        "USB Master"
        card        0
    }
}

pcm.!default {
    type            plug
    slave.pcm       "softvol"   #make use of softvol
}

```
The main card (VIA 8732) is used by MPD to broadcast 24/7 soft music to calm down my baby (I just receive it by radios around my house), and USB 3D sound is for default audio output now.
I tried connection the microphone to both of these devices, played with Multimedia System Selector and Gnome Alsa Mixer, nothing worked.

Any ideas?

---

### Post by VictorR on 2008-08-24
I got it working. What I missed in my previous searches was Sound option in System -> Preferences. The Audio Capture device was set to ALSA ... something, like all other devices, and it was wrong. I changed it to VIA 8237 (the card the microphone was attached to), and this fixed the problem.

---

### Post by Zabadda on 2008-08-25
ok i think maybe its might be my sound prefs that are wrong, though im not sure what shound card my laptop has, so i dont know which devices to choose in the drop downs.

---

### Post by Zabadda on 2008-08-25
ive managed to get this info in a terminal

head -n 1 /proc/asound/card0/codec*
==> /proc/asound/card0/codec#0 <==
Codec: Motorola Si3054

==> /proc/asound/card0/codec#1 <==
Codec: Realtek ALC880

not sure what do to with it tho lol

---

### Post by Zabadda on 2008-08-25
does anyone even know if this is just a driver problem or not? i can get sound on my speakers and headphones its JUST the mic that wont work. 

im having to swap back to XP to use games with the mic now so i need a fix so i can at last ditch it

---

### Post by Zabadda on 2008-08-25
sorry for the spam here ive also found this

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC880 Analog [ALC880 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC880 Digital [ALC880 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
zabadda@zabadda-laptop:~$ lspci -v
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
	Subsystem: Fujitsu Siemens Computers Unknown device 10b0
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: b0100000-b01fffff
	Prefetchable memory behind bridge: 00000000c0000000-00000000cfffffff
	Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
	Subsystem: Fujitsu Siemens Computers Unknown device 10b0
	Flags: bus master, fast devsel, latency 0, IRQ 21
	Memory at b0000000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=03, sec-latency=0
	Memory behind bridge: fac00000-febfffff
	Capabilities: <access denied>

00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	Memory behind bridge: b0200000-b02fffff
	Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Fujitsu Siemens Computers Unknown device 10b0
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 1800 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Fujitsu Siemens Computers Unknown device 10b0
	Flags: bus master, medium devsel, latency 0, IRQ 20
	I/O ports at 1820 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Fujitsu Siemens Computers Unknown device 10b0
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 1840 [size=32]

00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Fujitsu Siemens Computers Unknown device 10b0
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at 1860 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02) (prog-if 20 [EHCI])
	Subsystem: Fujitsu Siemens Computers Unknown device 10b0
	Flags: bus master, medium devsel, latency 0, IRQ 19
	Memory at b0004000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) (prog-if 01 [Subtractive decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=05, subordinate=05, sec-latency=32
	I/O behind bridge: 00003000-00003fff
	Memory behind bridge: b0300000-b03fffff
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
	Subsystem: Fujitsu Siemens Computers Unknown device 10b0
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>

00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02) (prog-if 8a [Master SecP PriP])
	Subsystem: Fujitsu Siemens Computers Unknown device 10b0
	Flags: bus master, medium devsel, latency 0, IRQ 20
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at 1880 [size=16]

00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02) (prog-if 01 [AHCI 1.0])
	Subsystem: Fujitsu Siemens Computers Unknown device 10b0
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 220
	I/O ports at 18c8 [size=8]
	I/O ports at 18ac [size=4]
	I/O ports at 18c0 [size=8]
	I/O ports at 18a8 [size=4]
	I/O ports at 18b0 [size=16]
	Memory at b0004400 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>

00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
	Subsystem: Fujitsu Siemens Computers Unknown device 10b0
	Flags: medium devsel, IRQ 10
	I/O ports at 18e0 [size=32]

01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility X1400 (prog-if 00 [VGA controller])
	Subsystem: Fujitsu Siemens Computers Unknown device 10b0
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at c0000000 (32-bit, prefetchable) [size=256M]
	I/O ports at 2000 [size=256]
	Memory at b0100000 (32-bit, non-prefetchable) [size=64K]
	[virtual] Expansion ROM at b0120000 [disabled] [size=128K]
	Capabilities: <access denied>

04:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
	Subsystem: Intel Corporation PRO/Wireless 3945ABG Network Connection
	Flags: bus master, fast devsel, latency 0, IRQ 219
	Memory at b0200000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

05:04.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link) (prog-if 10 [OHCI])
	Subsystem: Fujitsu Siemens Computers Unknown device 10b0
	Flags: bus master, medium devsel, latency 32, IRQ 18
	Memory at b0304000 (32-bit, non-prefetchable) [size=2K]
	Memory at b0300000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

05:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)
	Subsystem: Fujitsu Siemens Computers Unknown device 10b0
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 20
	I/O ports at 3000 [size=256]
	Memory at b0304800 (32-bit, non-prefetchable) [size=256]
	[virtual] Expansion ROM at b0320000 [disabled] [size=128K]
	Capabilities: <access denied>

---

### Post by Zabadda on 2008-08-27
does anyone even know if its just an Ubuntu problem?

---

### Post by markbuntu on 2008-08-27
There are some issues with setting up Intel HDA cards, this might help:


[http://ubuntuforums.org/showthread.php?t=616845](http://ubuntuforums.org/showthread.php?t=616845)

---

