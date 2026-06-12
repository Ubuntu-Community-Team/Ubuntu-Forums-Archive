---
title: "HDMI Audio Nvidia G310 Samsung P2570HD"
date: 2010-06-09
forum: Multimedia Software
---

### Post by linuxnovice on 2010-06-09
Hello,

I realize there are many threads dealing with audio over HDMI. However, none of the solutions/suggestions presented in them have worked for me. I have a GateWay DX483 ([http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=5602487&CatId=4928]("http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=5602487&CatId=4928")) with Nvidia G310 (which is the same as G210, I'm told) which has an HDMI port and also an audio chip on-board (I might be wrong on that though). I recently purchased Samsung P2570HD ([http://www.samsung.com/us/consumer/office/monitors/premium/LS25EMNKUY/ZA/index.idx?pagetype=prd_detail]("http://www.samsung.com/us/consumer/office/monitors/premium/LS25EMNKUY/ZA/index.idx?pagetype=prd_detail")) which has HDMI input. The monitor also has in-built speakers. I connected the computer to the monitor via the HDMI cable which came with the monitor. I could get the video to work without any problems. I used the nvidia-settings twinview to configure the monitors. However, as you might have guessed, I am not able to get the audio to go over the HDMI to the speakers on the monitors. 

I tried some of the suggestions given in other threads and messed up my already working audio and video once. I reverted back to what I had. In any case, I don't mind doing that again, so any help in fixing this problem is appreciated. I am also hoping that this thread can be helpful for others who are having similar problems. 

I am running 64-bit Ubuntu 10.04.

Thanks.

---

### Post by Jinger on 2010-06-09
I had had the same problem, but then I solved. Follow me:
Click on "System" left on the top then on preferences and in the end on "Audio". Audio configuration page will open:
[IMG]http://img3.imageshack.us/img3/8329/audiocz.png[/IMG]
Go to "Hardware" and at the bottom of the page there's "profile". Select "Digital Stereo (HDMI) output":
[IMG]http://img532.imageshack.us/img532/9041/audio1.png[/IMG]

---

### Post by linuxnovice on 2010-06-09
> **Jinger said:**
> I had had the same problem, but then I solved. Follow me:
Click on "System" left on the top then on preferences and in the end on "Audio". Audio configuration page will open:
Go to "Hardware" and at the bottom of the page there's "profile". Select "Digital Stereo (HDMI) output":


Thanks for your help. My problem is the HDMI doesn't even appear on the list of sound devices for me to select. Here are some outputs that might help:

```
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

```
lspci -v
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 12)
	Subsystem: Acer Incorporated [ALI] Device 0389
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: intel-agp

00:01.0 PCI bridge: Intel Corporation Core Processor PCI Express x16 Root Port (rev 12)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 0000c000-0000cfff
	Memory behind bridge: fa000000-fbdfffff
	Prefetchable memory behind bridge: 00000000ce000000-00000000dfffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
	Subsystem: Acer Incorporated [ALI] Device 0389
	Flags: bus master, fast devsel, latency 0, IRQ 10
	Memory at f9fffc00 (64-bit, non-prefetchable) [size=16]
	Capabilities: <access denied>

00:19.0 Ethernet controller: Intel Corporation 82578DC Gigabit Network Connection (rev 06)
	Subsystem: Acer Incorporated [ALI] Device 8000
	Flags: bus master, fast devsel, latency 0, IRQ 37
	Memory at f9fc0000 (32-bit, non-prefetchable) [size=128K]
	Memory at f9ffc000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at bc00 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: e1000e
	Kernel modules: e1000e

00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06) (prog-if 20)
	Subsystem: Acer Incorporated [ALI] Device 0389
	Flags: bus master, medium devsel, latency 0, IRQ 16
	Memory at f9ffa000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
	Subsystem: Acer Incorporated [ALI] Device 0389
	Flags: bus master, fast devsel, latency 0, IRQ 39
	Memory at f9ff4000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 00001000-00001fff
	Memory behind bridge: c0000000-c01fffff
	Prefetchable memory behind bridge: 00000000c0200000-00000000c03fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 06)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: fbe00000-fbefffff
	Prefetchable memory behind bridge: 00000000c0400000-00000000c05fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.2 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 (rev 06)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: c0600000-c07fffff
	Prefetchable memory behind bridge: 00000000c0800000-00000000c09fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.3 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 (rev 06)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
	I/O behind bridge: 00003000-00003fff
	Memory behind bridge: c0a00000-c0bfffff
	Prefetchable memory behind bridge: 00000000c0c00000-00000000c0dfffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 06)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
	I/O behind bridge: 00004000-00004fff
	Memory behind bridge: c0e00000-c0ffffff
	Prefetchable memory behind bridge: 00000000c1000000-00000000c11fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.6 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 7 (rev 06)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=07, subordinate=07, sec-latency=0
	I/O behind bridge: 00005000-00005fff
	Memory behind bridge: c1200000-c13fffff
	Prefetchable memory behind bridge: 00000000c1400000-00000000c15fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.7 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 8 (rev 06)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=08, subordinate=08, sec-latency=0
	I/O behind bridge: 00006000-00006fff
	Memory behind bridge: c1600000-c17fffff
	Prefetchable memory behind bridge: 00000000c1800000-00000000c19fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06) (prog-if 20)
	Subsystem: Acer Incorporated [ALI] Device 0389
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at f9ff8000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev a6) (prog-if 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=09, subordinate=09, sec-latency=32
	I/O behind bridge: 0000e000-0000efff
	Memory behind bridge: fbf00000-fbffffff
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 5 Series Chipset LPC Interface Controller (rev 06)
	Subsystem: Acer Incorporated [ALI] Device 0389
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: iTCO_wdt

00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 6 port SATA AHCI Controller (rev 06) (prog-if 01)
	Subsystem: Acer Incorporated [ALI] Device 0389
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 38
	I/O ports at b880 [size=8]
	I/O ports at b800 [size=4]
	I/O ports at b480 [size=8]
	I/O ports at b400 [size=4]
	I/O ports at b080 [size=32]
	Memory at f9ff2000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>
	Kernel driver in use: ahci
	Kernel modules: ahci

00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06)
	Subsystem: Acer Incorporated [ALI] Device 0389
	Flags: medium devsel, IRQ 11
	Memory at f9fff800 (64-bit, non-prefetchable) [size=256]
	I/O ports at 0400 [size=32]
	Kernel modules: i2c-i801

01:00.0 VGA compatible controller: nVidia Corporation GT218 [GeForce 310] (rev a2)
	Subsystem: PC Partner Limited Device 3100
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at fa000000 (32-bit, non-prefetchable) [size=16M]
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Memory at ce000000 (64-bit, prefetchable) [size=32M]
	I/O ports at cc00 [size=128]
	[virtual] Expansion ROM at fbd80000 [disabled] [size=512K]
	Capabilities: <access denied>
	Kernel driver in use: nvidia
	Kernel modules: nvidia, nvidiafb, nouveau

[B]01:00.1 Audio device: nVidia Corporation High Definition Audio Controller (rev a1)
	Subsystem: PC Partner Limited Device 3100
	Flags: bus master, fast devsel, latency 0, IRQ 40
	Memory at fbd7c000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel[/B]

03:00.0 SATA controller: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller (rev 03) (prog-if 01)
	Subsystem: Acer Incorporated [ALI] Device 0389
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at fbefe000 (32-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>
	Kernel driver in use: ahci
	Kernel modules: ahci

03:00.1 IDE interface: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller (rev 03) (prog-if 85 [Master SecO PriO])
	Subsystem: Acer Incorporated [ALI] Device 0389
	Flags: bus master, fast devsel, latency 0, IRQ 18
	I/O ports at dc00 [size=8]
	I/O ports at d880 [size=4]
	I/O ports at d800 [size=8]
	I/O ports at d480 [size=4]
	I/O ports at d400 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: pata_jmicron
	Kernel modules: pata_jmicron

09:06.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev c0) (prog-if 10)
	Subsystem: Acer Incorporated [ALI] Device 8010
	Flags: bus master, medium devsel, latency 64, IRQ 19
	Memory at fbfff800 (32-bit, non-prefetchable) [size=2K]
	I/O ports at ec00 [size=128]
	Capabilities: <access denied>
	Kernel driver in use: ohci1394
	Kernel modules: firewire-ohci, ohci1394

```

If you notice the device in bold above, lspci -v lists the NVidia HDMI audio as one of the audio devices, however this doesn't get listed in aplay -l.

---

### Post by Jinger on 2010-06-09
What version of Ubuntu do you use?

---

### Post by linuxnovice on 2010-06-09
> **Jinger said:**
> What version of Ubuntu do you use?

I am running 64-bit Ubuntu 10.04.

---

### Post by Jinger on 2010-06-09
Strange. You could solve your problem in another way:
Have you got a cable like this?
[IMG]http://www.angelipc.it/08112_0000.jpg[/IMG]

---

### Post by linuxnovice on 2010-06-09
> **Jinger said:**
> Strange. You could solve your problem in another way:
Have you got a cable like this?
[IMG]http://www.angelipc.it/08112_0000.jpg[/IMG]

No, I do not. But I can get one. Are you suggesting I hook up the audio from the PC to the Audio IN/OUT on the monitor through this cable?

Thanks.

---

### Post by Jinger on 2010-06-09
That cable is fantastic. Its acoustics aren't outstanding, but wherever you go you can connect it to everything you want because is a standard.

If you have a small problem with Nvidia driver you can't do anything because only they could solve that trouble. 

Would you mind telling me what model of PC you have?

---

### Post by lidex on 2010-06-09
Have you seen this:
[http://wiki.xbmc.org/index.php?title=HOW-TO_set_up_HDMI_audio_on_nVidia_GeForce_G210,_GT220,_or_GT240]("http://wiki.xbmc.org/index.php?title=HOW-TO_set_up_HDMI_audio_on_nVidia_GeForce_G210,_GT220,_or_GT240")

---

### Post by linuxnovice on 2010-06-10
> **Jinger said:**
> That cable is fantastic. Its acoustics aren't outstanding, but wherever you go you can connect it to everything you want because is a standard.

If you have a small problem with Nvidia driver you can't do anything because only they could solve that trouble. 

Would you mind telling me what model of PC you have?

If you look at my first post, it gives you a link from where I purchased my computer along with all its specifications. I'll include it here again for convenience. [http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=5602487&CatId=4928]("http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=5602487&CatId=4928")

> **lidex said:**
> Have you seen this:
[http://wiki.xbmc.org/index.php?title=HOW-TO_set_up_HDMI_audio_on_nVidia_GeForce_G210,_GT220,_or_GT240]("http://wiki.xbmc.org/index.php?title=HOW-TO_set_up_HDMI_audio_on_nVidia_GeForce_G210,_GT220,_or_GT240")

That looks really helpful. I will try it asap and post the results.

Thanks.

---

### Post by linuxnovice on 2010-06-10
I tried the suggestions given in the xmbc wiki page but I am still not able to get this to work. One update since last time is that I booted into Windows 7 ( I hadn't ever since I installed Ubuntu 10.04) and the Samsung monitor was automatically picked up and sound was redirected through the HDMI output automatically.

Also, I forgot to mention earlier that I have a dual monitor setup. The Samsung is attached to the HDMI port of the video card and I have a Dell 22" monitor attached to the VGA port of the video card.

---

