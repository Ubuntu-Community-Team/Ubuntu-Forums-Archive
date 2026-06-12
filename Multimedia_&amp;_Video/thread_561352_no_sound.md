---
title: "no sound"
date: 2007-09-27
forum: Multimedia &amp; Video
---

### Post by froman2686 on 2007-09-27
Okay, I attempted a couple of the fixes around here (reload alsa drivers, for example) but to no avail. My sound was working properly, there was nothing that happened when it suddenly stopped working. 

aplay -l output:
```
owner@owner-desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

lspci -v output (audio bolded):
```
owner@owner-desktop:~$ lspci -v
00:00.0 Host bridge: Intel Corporation 82P965/G965 Memory Controller Hub (rev 02)
        Subsystem: Intel Corporation Unknown device 514d
        Flags: bus master, fast devsel, latency 0
        Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation 82P965/G965 PCI Express Root Port (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        I/O behind bridge: 00002000-00002fff
        Memory behind bridge: e2000000-e4ffffff
        Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
        Capabilities: <access denied>

00:03.0 Communication controller: Intel Corporation 82P965/G965 HECI Controller (rev 02)
        Subsystem: Intel Corporation Unknown device 514d
        Flags: bus master, fast devsel, latency 0, IRQ 11
        Memory at e5325900 (64-bit, non-prefetchable) [size=16]
        Capabilities: <access denied>

00:19.0 Ethernet controller: Intel Corporation 82566DC Gigabit Network Connection (rev 02)
        Subsystem: Intel Corporation Unknown device 0001
        Flags: bus master, fast devsel, latency 0, IRQ 20
        Memory at e5300000 (32-bit, non-prefetchable) [size=128K]
        Memory at e5324000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at 30c0 [size=32]
        Capabilities: <access denied>

00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #4 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Intel Corporation Unknown device 514d
        Flags: bus master, medium devsel, latency 0, IRQ 16
        I/O ports at 30a0 [size=32]

00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #5 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Intel Corporation Unknown device 514d
        Flags: bus master, medium devsel, latency 0, IRQ 21
        I/O ports at 3080 [size=32]

00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI #2 (rev 02) (prog-if 20 [EHCI])
        Subsystem: Intel Corporation Unknown device 514d
        Flags: bus master, medium devsel, latency 0, IRQ 18
        Memory at e5325400 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

[B]00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
        Subsystem: Intel Corporation Unknown device 2504
        Flags: bus master, fast devsel, latency 0, IRQ 23
        Memory at e5320000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>[/B]

00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        Memory behind bridge: e5400000-e54fffff
        Capabilities: <access denied>

00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
        I/O behind bridge: 00001000-00001fff
        Memory behind bridge: e5200000-e52fffff
        Capabilities: <access denied>

00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
        Memory behind bridge: e5500000-e55fffff
        Capabilities: <access denied>

00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
        Memory behind bridge: e5600000-e56fffff
        Capabilities: <access denied>

00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
        Memory behind bridge: e5700000-e57fffff
        Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #1 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Intel Corporation Unknown device 514d
        Flags: bus master, medium devsel, latency 0, IRQ 22
        I/O ports at 3060 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #2 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Intel Corporation Unknown device 514d
        Flags: bus master, medium devsel, latency 0, IRQ 19
        I/O ports at 3040 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #3 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Intel Corporation Unknown device 514d
        Flags: bus master, medium devsel, latency 0, IRQ 18
        I/O ports at 3020 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI #1 (rev 02) (prog-if 20 [EHCI])
        Subsystem: Intel Corporation Unknown device 514d
        Flags: bus master, medium devsel, latency 0, IRQ 22
        Memory at e5325000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev f2) (prog-if 01 [Subtractive decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=07, subordinate=07, sec-latency=32
        Memory behind bridge: e5000000-e51fffff
        Prefetchable memory behind bridge: 00000000e0000000-00000000e1ffffff
        Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801HH (ICH8DH) LPC Interface Controller (rev 02)
        Subsystem: Intel Corporation Unknown device 514d
        Flags: bus master, medium devsel, latency 0
        Capabilities: <access denied>

00:1f.2 IDE interface: Intel Corporation 82801H (ICH8 Family) 4 port SATA IDE Controller (rev 02) (prog-if 8f [Master SecP SecO PriP PriO])
        Subsystem: Intel Corporation Unknown device 514d
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
        I/O ports at 3138 [size=8]
        I/O ports at 314c [size=4]
        I/O ports at 3130 [size=8]
        I/O ports at 3148 [size=4]
        I/O ports at 3110 [size=16]
        I/O ports at 3100 [size=16]
        Capabilities: <access denied>

00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
        Subsystem: Intel Corporation Unknown device 514d
        Flags: medium devsel, IRQ 10
        Memory at e5325800 (32-bit, non-prefetchable) [size=256]
        I/O ports at 3000 [size=32]

00:1f.5 IDE interface: Intel Corporation 82801H (ICH8 Family) 2 port SATA IDE Controller (rev 02) (prog-if 85 [Master SecO PriO])
        Subsystem: Intel Corporation Unknown device 514d
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
        I/O ports at 3128 [size=8]
        I/O ports at 3144 [size=4]
        I/O ports at 3120 [size=8]
        I/O ports at 3140 [size=4]
        I/O ports at 30f0 [size=16]
        I/O ports at 30e0 [size=16]
        Capabilities: <access denied>

01:00.0 VGA compatible controller: nVidia Corporation Unknown device 0400 (rev a1) (prog-if 00 [VGA])
        Subsystem: XFX Pine Group Inc. Unknown device 2280
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at e4000000 (32-bit, non-prefetchable) [size=16M]
        Memory at d0000000 (64-bit, prefetchable) [size=256M]
        Memory at e2000000 (64-bit, non-prefetchable) [size=32M]
        I/O ports at 2000 [size=128]
        Capabilities: <access denied>

03:00.0 IDE interface: Marvell Technology Group Ltd. Unknown device 6101 (rev b1) (prog-if 8f [Master SecP SecO PriP PriO])
        Subsystem: Marvell Technology Group Ltd. Unknown device 6101
        Flags: bus master, fast devsel, latency 0, IRQ 17
        I/O ports at 1018 [size=8]
        I/O ports at 1024 [size=4]
        I/O ports at 1010 [size=8]
        I/O ports at 1020 [size=4]
        I/O ports at 1000 [size=16]
        Memory at e5200000 (32-bit, non-prefetchable) [size=512]
        Capabilities: <access denied>

07:01.0 Multimedia controller: ATI Technologies Inc Unknown device 4d52
        Subsystem: ATI Technologies Inc Unknown device a346
        Flags: bus master, medium devsel, latency 32, IRQ 9
        Memory at e5000000 (32-bit, non-prefetchable) [size=1M]
        Memory at e0000000 (32-bit, prefetchable) [size=32M]
        Capabilities: <access denied>

07:02.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)
        Subsystem: Netgear Unknown device 5a00
        Flags: bus master, medium devsel, latency 168, IRQ 18
        Memory at e5100000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>

07:03.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link) (prog-if 10 [OHCI])
        Subsystem: Intel Corporation Unknown device 514d
        Flags: bus master, medium devsel, latency 32, IRQ 19
        Memory at e5114000 (32-bit, non-prefetchable) [size=2K]
        Memory at e5110000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

```

To my knowledge I was running sigmatel drivers...or the oss mixer. I'm using the optical output. Again, this was all working properly and stopped for no discernable reason, and will not restart even after complete shutdown and cold boot. Does anyone have any suggestion for how I can rectify this?

---

### Post by gwoodard on 2007-09-27
Just a thought is this onboard or are u using a sound card? (PCI)

---

### Post by froman2686 on 2007-09-27
Yes, it's built right into the motherboard.

---

### Post by gwoodard on 2007-09-27
what im talking about do u own a sound card and using onboard or just onboard?

---

### Post by froman2686 on 2007-09-27
no, it's strictly onboard sound. there are no other sound cards but the one that's built into the motherboard.

---

### Post by gwoodard on 2007-09-27
ok then try reinstalling ubuntu and update and do not mess with the sound settings

BTW What Ubuntu version do u have?

---

### Post by froman2686 on 2007-09-27
it's Feisty, just updated to the latest kernel (i basically let autoupdate handle it...still new to linux and all)

is there any way to reinstall without formatting the partition? i don't want to nuke all my settings and saved information just because my sound crapped out on me.

I'm also not convinced reinstalling is the only way to fix this...perhaps more background would help?

My sound troubles started when I was using WINE - specifically, to play NetStorm (if it matters). After playing the game, then closing it, my sound would sometimes not come back, forcing a restart. This worked a couple of times, but now no longer solves the issue. Despite many restarts, as well as attempting to play with OSS and ALSA settings (by following guides, of course) I still have been unable to resurrect my sound. I have purged and reinstalled ALSA, and have also installed the ALSA-OSS  compatibility pack off synaptic. Restarted, still no good. I have attempted to change my sound settings from "STAC92xx Digital" to "autodetect," "alsa," and "oss" but that also hasn't helped.

---

### Post by gwoodard on 2007-09-27
wait try winecfg in terminal and go to sound and select "OSS" or whatever it claims is default or right click on your speaker and go to "volume control" then file then change device to your sound device or see if your master is muted or unmuted and about 3/4 all the way up

---

### Post by froman2686 on 2007-09-27
Tried both, any sound driver selection in winecfg doesn't seem to make much difference, and oh how i wish it were as simple as accidental muting haha. 

No dice on either - winecfg doesn't cooperate no matter what sound settings, and the volume's cranked all the way.

---

### Post by froman2686 on 2007-09-28
Maybe more information can help?

tail -2 /proc/asound/oss/sndstat output:
```
Mixers:
0: SigmaTel STAC9271D

```

asoundconf -list output:
```
Names of available sound cards:
Intel
```

aplay -l output:
```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

cat /proc/interrupts output;
```
           CPU0       CPU1       
  0:   16791078          0   IO-APIC-edge      timer
  1:          2          0   IO-APIC-edge      i8042
  7:          0          0   IO-APIC-edge      parport0
  8:          3          0   IO-APIC-edge      rtc
  9:          1          0   IO-APIC-fasteoi   acpi
 12:     243206     268580   IO-APIC-edge      i8042
 16:    6258510    6426997   IO-APIC-fasteoi   uhci_hcd:usb1, nvidia
 17:       2334     167292   IO-APIC-fasteoi   libata
 18:    5465088    9578019   IO-APIC-fasteoi   uhci_hcd:usb5, ehci_hcd:usb6, wifi0
 19:      48493      56257   IO-APIC-fasteoi   ohci1394, uhci_hcd:usb4, libata, libata
 20:          0          0   IO-APIC-fasteoi   uhci_hcd:usb2
 21:    1990477          0   IO-APIC-fasteoi   uhci_hcd:usb3, ehci_hcd:usb7
 22:     151875      90131   IO-APIC-fasteoi   eth0
 23:    1149128          0   IO-APIC-fasteoi   HDA Intel
NMI:          0          0 
LOC:   16788679   16788660 
ERR:          0
MIS:          0
```

I've tried uninstalling and rebuilding the ALSA drivers, utils, and libs from the latest snapshot, didn't work so I reverted to stable...really willing to do anything to not have to reformat here.

---

