---
title: "NO SOUND in jaunty"
date: 2009-05-18
forum: Multimedia Software
---

### Post by jdunn on 2009-05-18
I followed the comprehensive audio guide but haven't had much success.  I have an HP Pavilion laptop.  The sound worked through the speakers when I had Intrepid x64 installed.  I made a clean install-over of Jaunty x64 and now I can only get sound through the headphones.

aplay -l

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

lspci -v

```
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
	Subsystem: Hewlett-Packard Company Device 3603
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: intel-agp

00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 00009000-00009fff
	Memory behind bridge: d0000000-d2ffffff
	Prefetchable memory behind bridge: 00000000c0000000-00000000cfffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
	Subsystem: Hewlett-Packard Company Device 3603
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at a0e0 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
	Subsystem: Hewlett-Packard Company Device 3603
	Flags: bus master, medium devsel, latency 0, IRQ 21
	I/O ports at a0c0 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03) (prog-if 20)
	Subsystem: Hewlett-Packard Company Device 3603
	Flags: bus master, medium devsel, latency 0, IRQ 19
	Memory at df305c00 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
	Subsystem: Hewlett-Packard Company Device 3621
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at df300000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 00008000-00008fff
	Memory behind bridge: de200000-df2fffff
	Prefetchable memory behind bridge: 00000000d3000000-00000000d3ffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	I/O behind bridge: 00006000-00007fff
	Memory behind bridge: dd200000-de1fffff
	Prefetchable memory behind bridge: 00000000d4000000-00000000d50fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	I/O behind bridge: 00005000-00005fff
	Memory behind bridge: dc200000-dd1fffff
	Prefetchable memory behind bridge: 00000000d5100000-00000000d60fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
	I/O behind bridge: 00004000-00004fff
	Memory behind bridge: db200000-dc1fffff
	Prefetchable memory behind bridge: 00000000d6100000-00000000d70fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
	I/O behind bridge: 00003000-00003fff
	Memory behind bridge: da100000-db1fffff
	Prefetchable memory behind bridge: 00000000d7100000-00000000d80fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=07, subordinate=09, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: d9100000-da0fffff
	Prefetchable memory behind bridge: 00000000d8100000-00000000d90fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
	Subsystem: Hewlett-Packard Company Device 3603
	Flags: bus master, medium devsel, latency 0, IRQ 20
	I/O ports at a0a0 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
	Subsystem: Hewlett-Packard Company Device 3603
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at a080 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
	Subsystem: Hewlett-Packard Company Device 3603
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at a060 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
	Subsystem: Hewlett-Packard Company Device 3603
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at a040 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03) (prog-if 20)
	Subsystem: Hewlett-Packard Company Device 3603
	Flags: bus master, medium devsel, latency 0, IRQ 20
	Memory at df305800 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93) (prog-if 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=0a, subordinate=0a, sec-latency=32
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
	Subsystem: Hewlett-Packard Company Device 3603
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: iTCO_wdt

00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03) (prog-if 01)
	Subsystem: Hewlett-Packard Company Device 3603
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 2296
	I/O ports at a108 [size=8]
	I/O ports at a114 [size=4]
	I/O ports at a100 [size=8]
	I/O ports at a110 [size=4]
	I/O ports at a020 [size=32]
	Memory at df305000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>
	Kernel driver in use: ahci

00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
	Subsystem: Hewlett-Packard Company Device 3603
	Flags: medium devsel, IRQ 11
	Memory at df306000 (64-bit, non-prefetchable) [size=256]
	I/O ports at a000 [size=32]
	Kernel modules: i2c-i801

00:1f.6 Signal processing controller: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem (rev 03)
	Subsystem: Hewlett-Packard Company Device 3603
	Flags: fast devsel, IRQ 11
	Memory at df304000 (64-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

01:00.0 VGA compatible controller: nVidia Corporation GeForce 9200M GS (rev a1)
	Subsystem: Hewlett-Packard Company Device 3603
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at d2000000 (32-bit, non-prefetchable) [size=16M]
	Memory at c0000000 (64-bit, prefetchable) [size=256M]
	Memory at d0000000 (64-bit, non-prefetchable) [size=32M]
	I/O ports at 9000 [size=128]
	Capabilities: <access denied>
	Kernel driver in use: nvidia
	Kernel modules: nvidia, nvidiafb

02:00.0 Network controller: Intel Corporation PRO/Wireless 5100 AGN [Shiloh] Network Connection
	Subsystem: Intel Corporation Device 1211
	Flags: bus master, fast devsel, latency 0, IRQ 2294
	Memory at de200000 (64-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>
	Kernel driver in use: iwlagn
	Kernel modules: iwlagn

03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
	Subsystem: Hewlett-Packard Company Device 3603
	Flags: bus master, fast devsel, latency 0, IRQ 2295
	I/O ports at 6000 [size=256]
	Memory at d4010000 (64-bit, prefetchable) [size=4K]
	Memory at d4000000 (64-bit, prefetchable) [size=64K]
	Expansion ROM at d4020000 [disabled] [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: r8169
	Kernel modules: r8169

06:00.0 FireWire (IEEE 1394): JMicron Technologies, Inc. IEEE 1394 Host Controller (prog-if 10)
	Subsystem: Hewlett-Packard Company Device 3603
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at da100000 (32-bit, non-prefetchable) [size=2K]
	Memory at da100d00 (32-bit, non-prefetchable) [size=128]
	Memory at da100c80 (32-bit, non-prefetchable) [size=128]
	Memory at da100c00 (32-bit, non-prefetchable) [size=128]
	Capabilities: <access denied>
	Kernel driver in use: ohci1394
	Kernel modules: firewire-ohci, ohci1394

06:00.1 System peripheral: JMicron Technologies, Inc. SD/MMC Host Controller
	Subsystem: Hewlett-Packard Company Device 3603
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at da100b00 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: sdhci-pci
	Kernel modules: sdhci-pci

06:00.2 SD Host controller: JMicron Technologies, Inc. Standard SD Host Controller (prog-if 01)
	Subsystem: Hewlett-Packard Company Device 3603
	Flags: fast devsel, IRQ 16
	Memory at da100a00 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel modules: sdhci-pci

06:00.3 System peripheral: JMicron Technologies, Inc. MS Host Controller
	Subsystem: Hewlett-Packard Company Device 3603
	Flags: bus master, fast devsel, latency 0, IRQ 11
	Memory at da100900 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

06:00.4 System peripheral: JMicron Technologies, Inc. xD Host Controller
	Subsystem: Hewlett-Packard Company Device 3603
	Flags: bus master, fast devsel, latency 0, IRQ 11
	Memory at da100800 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

```

I also ran alsamixer and didn't see that any sound output was muted.

Please help.

---

### Post by philcamlin on 2009-05-18
ahh i had the same problem earlier today 
if you click on the sound icon in the top right hand corner 
unmute everything and change all dials theough every tab to 100% 

one oof my intel onboard audio thinks was at 0 for me so my sound works now 

hope i helped:p

---

### Post by JK3mp on 2009-05-18
I would check ALL your sound settings... also are you using ALSA? or something like OSS or Pulse etc...

---

### Post by jdunn on 2009-05-18
> **philcamlin said:**
> ahh i had the same problem earlier today 
if you click on the sound icon in the top right hand corner 
unmute everything and change all dials theough every tab to 100% 

one oof my intel onboard audio thinks was at 0 for me so my sound works now 

hope i helped:p

I'm afraid it didn't help.  None of the sound was muted.  The only volume sliders I have are Master, headphone, PCM and Front.

Also, on 8.10 I was able to control volume with the laptop volume control buttons.  No can do with 9.04.

---

### Post by jdunn on 2009-05-18
> **JK3mp said:**
> I would check ALL your sound settings... also are you using ALSA? or something like OSS or Pulse etc...

Well, I've checked System>Preferences>Sound from the desktop panel.  The devices tab shows everything as "autodetect" except for Sound Capture, which is "ALSA".  The device is Capture:HDA Intel -  STAC92XX Analog (Pulse)

I've checked volume control.  Device is "HDA Intel (ALSA Mixer)".  I've tried enabling everything in preferences.  Still no luck.

---

### Post by zefiriss01 on 2009-05-18
i have same problem, i use intel onboard, this post solved it. 

> **philcamlin said:**
> if you click on the sound icon in the top right hand corner 
unmute everything and change all dials through every tab to 100%

but really annoying i have to click it each time start.

---

### Post by jdunn on 2009-05-19
Bump

---

### Post by jdunn on 2009-05-19
bump

---

### Post by enz1m3 on 2009-05-19
have you tried to change the "default" sound device in there? clicking the test sound button what do you get? the "autodetect" plays any sound at all?

---

### Post by jdunn on 2009-05-20
> **enz1m3 said:**
> have you tried to change the "default" sound device in there? clicking the test sound button what do you get? the "autodetect" plays any sound at all?

Makes no difference.  I still get no sound, except through headphones.  However, if I select HDA Intel Stac 92xx Analog (ALSA), I get the following message when I test:  audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback.

---

### Post by enz1m3 on 2009-05-20
are you 100% sure you have nothing muted on your devices? (check preferences and tick everything in there for playback) because if you get sound through headphones then there is no drivers problem for the soundcard...

---

### Post by jdunn on 2009-05-20
> **enz1m3 said:**
> are you 100% sure you have nothing muted on your devices? (check preferences and tick everything in there for playback) because if you get sound through headphones then there is no drivers problem for the soundcard...

You mean select "preferences" from the volume control applet?  Not only did I try enabling visibility of every track.  I made sure none were muted and all were maximum volume...I've also tried switching to Analog Mux instead of digital for the IEC958 playback source.  I've even rebooted after changes.  It makes no difference.

I've also tried alsamixer.  Unmuting analog loopbacks turns the sound off completely.  Other than that, I still get no speaker sound.

It must be a driver problem.  On 8.10, I could control the volume with my laptop volume controls, whether sound came from speakers or headphones.  On 9.04., the laptop volume controls don't work.

One more thing.  The sound through headphones is crisper and clearer on 9.04 than it ever was through 8.10 or even through Vista.  It almost seems like there is more than one sound device and 9.04 is using the wrong one.  however, I can't find another device from aplay or lspci.

---

### Post by enz1m3 on 2009-05-20
Ok, I believe you should post this as a bug on launchpad then.

---

### Post by TheBootstrapKid on 2009-05-20
i just bought an hp pavilion laptop and i am having the same issue

---

### Post by jdunn on 2009-05-20
> **enz1m3 said:**
> Ok, I believe you should post this as a bug on launchpad then.

Already have...twice, in the last week.  That should be enough, I hope.

---

### Post by jdunn on 2009-05-24
Someone game me this solution, which works.

[http://ubuntuforums.org/showthread.php?p=7337387#post7337387]("http://ubuntuforums.org/showthread.php?p=7337387#post7337387")

However, now the mic doesn't work.  That's okay...I can live without the mic until 9.10

---

