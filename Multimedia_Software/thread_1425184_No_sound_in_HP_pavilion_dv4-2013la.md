---
title: "No sound in HP pavilion dv4-2013la"
date: 2010-03-08
forum: Multimedia Software
---

### Post by X1R1 on 2010-03-08
Hi, this is one of those "I have no sound after installation" threads. I hope you can help me out, I followed the stickied comprehensive sound problems solutions guide and had no luck.

Then I googled and found that I can add this line at /etc/modprobe.d/alsa-base.conf:

> options snd-hda-intel model=hp-m4 enable_msi=1

But that also didnt work-

Output from aplay and lspci:

aplay

```
ax@HPDV4UBUNTU:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

lspci

```
ax@HPDV4UBUNTU:~$ lspci -v
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge Alternate
	Subsystem: Hewlett-Packard Company Device 3642
	Flags: bus master, 66MHz, medium devsel, latency 0
	Capabilities: <access denied>

00:01.0 PCI bridge: Hewlett-Packard Company Device 9602
	Flags: bus master, 66MHz, medium devsel, latency 64
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 00007000-00007fff
	Memory behind bridge: d2300000-d24fffff
	Prefetchable memory behind bridge: 00000000c0000000-00000000cfffffff
	Capabilities: <access denied>
	Kernel modules: shpchp

00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=07, sec-latency=0
	I/O behind bridge: 00003000-00006fff
	Memory behind bridge: d1300000-d22fffff
	Prefetchable memory behind bridge: 00000000d0000000-00000000d0ffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=08, subordinate=08, sec-latency=0
	Memory behind bridge: d1200000-d12fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=09, subordinate=09, sec-latency=0
	Memory behind bridge: d1100000-d11fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:07.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=0a, subordinate=0a, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: b0000000-b00fffff
	Prefetchable memory behind bridge: 00000000d1000000-00000000d10fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode] (prog-if 01)
	Subsystem: Hewlett-Packard Company Device 3642
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 29
	I/O ports at 8038 [size=8]
	I/O ports at 804c [size=4]
	I/O ports at 8030 [size=8]
	I/O ports at 8048 [size=4]
	I/O ports at 8010 [size=16]
	Memory at d2508000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ahci

00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller (prog-if 10)
	Subsystem: Hewlett-Packard Company Device 3642
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
	Memory at d2507000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller (prog-if 10)
	Subsystem: Hewlett-Packard Company Device 3642
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
	Memory at d2506000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller (prog-if 20)
	Subsystem: Hewlett-Packard Company Device 3642
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
	Memory at d2508500 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller (prog-if 10)
	Subsystem: Hewlett-Packard Company Device 3642
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
	Memory at d2505000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller (prog-if 10)
	Subsystem: Hewlett-Packard Company Device 3642
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
	Memory at d2504000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller (prog-if 20)
	Subsystem: Hewlett-Packard Company Device 3642
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
	Memory at d2508400 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3c)
	Subsystem: Hewlett-Packard Company Device 3642
	Flags: 66MHz, medium devsel
	Capabilities: <access denied>
	Kernel driver in use: piix4_smbus
	Kernel modules: i2c-piix4

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
	Subsystem: Hewlett-Packard Company Device 3642
	Flags: bus master, slow devsel, latency 64, IRQ 16
	Memory at d2500000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
	Subsystem: Hewlett-Packard Company Device 3642
	Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (prog-if 01)
	Flags: bus master, 66MHz, medium devsel, latency 64
	Bus: primary=00, secondary=0b, subordinate=0b, sec-latency=64

00:18.0 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] HyperTransport Configuration
	Flags: fast devsel
	Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Address Map
	Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] DRAM Controller
	Flags: fast devsel
	Kernel modules: amd64_edac_mod

00:18.3 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Miscellaneous Control
	Flags: fast devsel
	Capabilities: <access denied>

00:18.4 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Link Control
	Flags: fast devsel

01:05.0 VGA compatible controller: ATI Technologies Inc Device 9712
	Subsystem: Hewlett-Packard Company Device 3642
	Flags: bus master, fast devsel, latency 0, IRQ 31
	Memory at c0000000 (32-bit, prefetchable) [size=256M]
	I/O ports at 7000 [size=256]
	Memory at d2400000 (32-bit, non-prefetchable) [size=64K]
	Memory at d2300000 (32-bit, non-prefetchable) [size=1M]
	Capabilities: <access denied>
	Kernel driver in use: fglrx_pci
	Kernel modules: fglrx, radeon

01:05.1 Audio device: ATI Technologies Inc Device 970f
	Subsystem: Hewlett-Packard Company Device 3642
	Flags: bus master, fast devsel, latency 0, IRQ 19
	Memory at d2410000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

09:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
	Subsystem: Hewlett-Packard Company Device 3040
	Flags: bus master, fast devsel, latency 0, IRQ 18
	Memory at d1100000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: ath9k
	Kernel modules: ath9k

0a:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
	Subsystem: Hewlett-Packard Company Device 3642
	Flags: bus master, fast devsel, latency 0, IRQ 30
	I/O ports at 2000 [size=256]
	Memory at d1010000 (64-bit, prefetchable) [size=4K]
	Memory at d1000000 (64-bit, prefetchable) [size=64K]
	Expansion ROM at d1020000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: r8169
	Kernel modules: r8169

```

system Specs:

AMD Athlon II Dual Core M300
3GB of RAM
Kernel 2.6.31-20

Running Ubuntu Karmic Koala 64bit

Thanks in advance for the help

---

### Post by Jackelope King on 2010-03-08
If you have a pair of headphones handy, can you check to see if your front headphone jacks will successfully produce sound?

---

### Post by X1R1 on 2010-03-08
indeed, with headphones plugged in I get sound, pretty weird!

And as weird as it sounds, After I unplugged the headphones now sound is coming out from the laptop speakers! lol

---

### Post by Jackelope King on 2010-03-08
This worked for me on my **dv3510nr**, but the problem you describe is exactly the problem I had. If you continue to have problems, you can try this.

Depending on your model, it might not do the trick, so back up a copy of your alsa-base.conf file first.

From [this thread]("http://ubuntuforums.org/showthread.php?t=1258788"):

> **dannymac64 said:**
> After spending many, many hours searching for solutions concerning my dv3-2155mx (Jaunty 9.04 64 bit), I thought I'd post my successes in hopes that it would help someone:

Flawless sound and internal mic functionality:
1. Install the latest ALSA drivers.  I installed 1.0.20 via this link, but watch out for his tar extract commands, which didn't work for me:
[http://monespaceperso.org/blog-en/2009/05/09/upgrade-alsa-1020-on-ubuntu-jaunty-904/](http://monespaceperso.org/blog-en/2009/05/09/upgrade-alsa-1020-on-ubuntu-jaunty-904/)

2. Edit alsa-base.conf:
```
sudo gedit /etc/modprobe.d/alsa-base.conf
```
3. Then add (note the model is **hp-dv5**):
```
options snd-hda-intel model=hp-dv5 enable_msi=1
```


---

### Post by X1R1 on 2010-03-08
ok now, sound works flawlessly with ONE user and DOES NOT WORK with the other user, i checked groups and the user having the problem has correct permissions.

What can i do here?

regards

---

### Post by RedSingularity on 2010-03-11
Under the user having the problem try this in a terminal

alsamixer

and make sure all the levels are up.

---

### Post by X1R1 on 2010-03-11
> **RedSingularity said:**
> Under the user having the problem try this in a terminal

alsamixer

and make sure all the levels are up.

thanks for your reply redsingularity, however, I have checked that already and all volumes are up. thats the weird thing forgot to mention it on the previous post.

any other thing I can try?

---

### Post by RedSingularity on 2010-03-13
Post the output of this command if there is any......

cat /etc/modprobe.d/blacklist.conf

---

### Post by X1R1 on 2010-03-13
Here is the output:

> ax@HPDV4UBUNTU:~$ cat /etc/modprobe.d/blacklist.conf

# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac


regards

UPDATE: Problem Solved, turns out that on that user the wrong device was specified for sound output (no idea why another device appeared If this laptop has only 1 sound card....)

Nevertheless, Im curious in what was that output for? can you explain singularity?

---

### Post by RedSingularity on 2010-03-13
I am afraid i cannot explain that one to you.  Though it is not a rare happening, i have had the same thing happen to me in the past.  Glad you got it working though.

---

### Post by Rey Templario on 2011-09-01
Hi there,

I installed Ubuntu 10.10 in my HP pavilion dv6100, everything was working, but after 3 months my sound is not working well. The problem is intermittent meaning that some days I got sound, but most of the time the computer does not play any sound, with or without headphones. I have tried whatever thread in this and other forums without luck. I know it is not hardware problem.

Hope you can help me.

---

