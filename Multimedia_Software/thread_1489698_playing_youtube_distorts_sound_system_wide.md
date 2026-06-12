---
title: "playing youtube distorts sound system wide"
date: 2010-05-21
forum: Multimedia Software
---

### Post by kingsrule5 on 2010-05-21
I am running a toshiba NB305 with 10.04 Netbook edition and I am having an issue with my sound where it will play perfectly clear in VLC, SMplayer and even in google video. All system tones play nice and clear. Then when i play a video in youtube the sound distort and all sounds system wide get distorted, scratchy and sound like the speakers are blown. If I restart then things go back to normal.

Also i played 1 quick youtube video (the connan obrien 5 year anny on the main page if anybody wants to test) and i was fine then i hit the next video (csi miami endless one liners) and it distorted like crazy. Then all sound effects system wide got distorted. Also it effects both speakers and headphones

These are the things i have tried so far based on other threads:

```
sudo apt-get update
sudo-apt upgrade
sudo apt-get install --reinstall alsa-utils alsa-oss alsa-base libasound2 libasound2-plugins linux-sound-base gstreamer0.10-alsa

```

So far youtube is the only thing i have found to trigger the issue but i only found the issue in the past few hours.

I am still new to Ubuntu so i don't know what else to try but if you guys tell me what diagnostic stuff to do i can run it.

Other possible helpful info:
Toshiba NB305 netbook 1.40 bios
dual boot with Win 7 pro (sound works fine in win7)
Have run all latest package updates
Youtube set to run at HD quality automatically

Thanks in advance

---

### Post by ipatfrmww on 2010-05-21
What flash player are you using?

---

### Post by kingsrule5 on 2010-05-21
honestly not sure i do have java installed. Is there a way to check?

I am running google chrome which i believe is adobe enabled.

---

### Post by lidex on 2010-05-21
Go here and use flash installer to remove old flash versions and install latest:
[http://ubuntuforums.org/showthread.php?t=1414595]("http://ubuntuforums.org/showthread.php?t=1414595")
Close your browser before running. Then run this command:
```
sudo ln -s /usr/lib/mozilla/plugins /opt/google/chrome/plugins
```
In a Terminal="Applications->Accessories->Terminal"

---

### Post by kingsrule5 on 2010-05-21
followed all that including removing flash first and then trying again but the same issue exists

---

### Post by pwaugh on 2010-05-21
Are you running 64-bit?  

If so, I used this link to successfully install Flash:

[http://labs.adobe.com/downloads/flashplayer10_64bit.html](http://labs.adobe.com/downloads/flashplayer10_64bit.html)

Patrick

---

### Post by kingsrule5 on 2010-05-21
not running 64bit cant do it on the atom.

But tried again with the flash removal/add and the terminal command again and it seems to work now but some songs still sound weird on youtube but i think it has to do with the actual speakers and video quality.

The first time the terminal command didn't produce anything but it did the 2nd so that may have been the issue.

thanks guys


edit: ok so it as false hope now it limits the issue to within chrome as vlc still sounds fne but videos on youtube and msn distort now.

---

### Post by kingsrule5 on 2010-05-21
ok i have seen these asked for in numerous other threads so i will throw the results up

```
~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC272 Analog [ALC272 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

```

```
jared@UbuntuNetbook:~$ lspci -v
00:00.0 Host bridge: Intel Corporation N10 Family DMI Bridge
	Subsystem: Toshiba America Info Systems Device ff00
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller
	Subsystem: Toshiba America Info Systems Device ff30
	Flags: bus master, fast devsel, latency 0, IRQ 29
	Memory at f0200000 (32-bit, non-prefetchable) [size=512K]
	I/O ports at 18d0 [size=8]
	Memory at d0000000 (32-bit, prefetchable) [size=256M]
	Memory at f0000000 (32-bit, non-prefetchable) [size=1M]
	Capabilities: <access denied>
	Kernel driver in use: i915
	Kernel modules: i915

00:02.1 Display controller: Intel Corporation N10 Family Integrated Graphics Controller
	Subsystem: Toshiba America Info Systems Device ff30
	Flags: bus master, fast devsel, latency 0
	Memory at f0280000 (32-bit, non-prefetchable) [size=512K]
	Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
	Subsystem: Toshiba America Info Systems Device ff00
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at 80a00000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
	I/O behind bridge: 00003000-00003fff
	Memory behind bridge: 80000000-801fffff
	Prefetchable memory behind bridge: 0000000080200000-00000000803fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=07, subordinate=07, sec-latency=0
	I/O behind bridge: 00004000-00004fff
	Memory behind bridge: f0100000-f01fffff
	Prefetchable memory behind bridge: 0000000080400000-00000000805fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=09, subordinate=09, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: 80600000-809fffff
	Prefetchable memory behind bridge: 00000000f0500000-00000000f05fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 02)
	Subsystem: Toshiba America Info Systems Device ff00
	Flags: bus master, medium devsel, latency 0, IRQ 23
	I/O ports at 1820 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
	Subsystem: Toshiba America Info Systems Device ff00
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 1840 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
	Subsystem: Toshiba America Info Systems Device ff00
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 1860 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
	Subsystem: Toshiba America Info Systems Device ff00
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at 1880 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02) (prog-if 20)
	Subsystem: Toshiba America Info Systems Device ff00
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at 80a04000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) (prog-if 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=11, subordinate=11, sec-latency=32
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
	Subsystem: Toshiba America Info Systems Device ff00
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>

00:1f.2 SATA controller: Intel Corporation N10/ICH7 Family SATA AHCI Controller (rev 02) (prog-if 01)
	Subsystem: Toshiba America Info Systems Device ff00
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 28
	I/O ports at 18e8 [size=8]
	I/O ports at 18dc [size=4]
	I/O ports at 18e0 [size=8]
	I/O ports at 18d8 [size=4]
	I/O ports at 18c0 [size=16]
	Memory at 80a04400 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ahci
	Kernel modules: ahci

00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
	Subsystem: Toshiba America Info Systems Device ff00
	Flags: medium devsel, IRQ 10
	I/O ports at 18a0 [size=32]
	Kernel modules: i2c-i801

07:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
	Subsystem: Accton Technology Corporation Device e811
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at f0100000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: ath9k
	Kernel modules: ath9k

09:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
	Subsystem: Toshiba America Info Systems Device ff30
	Flags: bus master, fast devsel, latency 0, IRQ 27
	I/O ports at 2000 [size=256]
	Memory at f0520000 (64-bit, prefetchable) [size=4K]
	Memory at f0510000 (64-bit, prefetchable) [size=64K]
	[virtual] Expansion ROM at f0540000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: r8169
	Kernel modules: r8169

```

---

### Post by jim_charlton on 2010-05-27
This is a known issue with the NB305.  If you are using "nohz=off highres=off" on the GRUB kernel line, this bug will bite you.
See
[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/574137](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/574137)

---

