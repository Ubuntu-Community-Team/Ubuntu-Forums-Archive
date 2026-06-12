---
title: "Please help me enable sound on Ubuntu 9.04 with a Creative SB Audigy SE"
date: 2009-05-17
forum: Multimedia Software
---

### Post by 0xbyte on 2009-05-17
I don't exactly know a lot about Linux, and am rather new at Ubuntu. I have a Creative Sound Blaster Audigy SE which works fine in Windows and is seat properly in a slot on the motherboard. I am as certain as I can be that nothing is wrong with the card itself. The card was a replacement for the onboard sound which became corrupted (crackling and popping sounds) some time ago. I've since disabled the onboard sound through the BIOS.

I could have conflicting audio software on Ubuntu. As far as I know, I have not installed anything but PulseAudio; I installed it in hopes it would find and read the soundcard.

Basically I am at a loss to figure out which command to run in order to check if something is wrong. So if one thinks that they can help me, just tell me what do and I'll return the results as best I can. I would really appreciate the help, I am at wits end trying to figure out how to pull this off myself.

---

### Post by 0xbyte on 2009-05-17
This was requested on IRC:

$ aplay -l
```
**** List of PLAYBACK Hardware Devices ****
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
```$ lspci -v
```
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
    Subsystem: Dell Device 019d
    Flags: bus master, fast devsel, latency 0
    Memory at f0000000 (32-bit, prefetchable) [size=128M]
    Capabilities: <access denied>
    Kernel driver in use: agpgart-intel
    Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
    Subsystem: Dell Device 019d
    Flags: fast devsel, IRQ 11
    Memory at e8000000 (32-bit, prefetchable) [size=128M]
    Memory at feb80000 (32-bit, non-prefetchable) [size=512K]
    I/O ports at efa8 [size=8]
    Capabilities: <access denied>
    Kernel modules: intelfb

00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
    Subsystem: Dell Device 019d
    Flags: bus master, medium devsel, latency 0, IRQ 16
    I/O ports at ff80 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
    Subsystem: Dell Device 019d
    Flags: bus master, medium devsel, latency 0, IRQ 19
    I/O ports at ff60 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
    Subsystem: Dell Device 019d
    Flags: bus master, medium devsel, latency 0, IRQ 16
    I/O ports at ff20 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02) (prog-if 20)
    Subsystem: Dell Device 019d
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at ffa80800 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
    I/O behind bridge: 0000d000-0000dfff
    Memory behind bridge: fea00000-feafffff
    Kernel modules: shpchp

00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
    Flags: bus master, medium devsel, latency 0
    Kernel modules: iTCO_wdt, intel-rng

00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02) (prog-if 8a [Master SecP PriP])
    Subsystem: Dell Device 019d
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at 01f0 [size=8]
    I/O ports at 03f4 [size=1]
    I/O ports at 0170 [size=8]
    I/O ports at 0374 [size=1]
    I/O ports at ffa0 [size=16]
    Memory at feb7fc00 (32-bit, non-prefetchable) [size=1K]
    Kernel driver in use: ata_piix

00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
    Subsystem: Dell Device 019d
    Flags: medium devsel, IRQ 3
    I/O ports at efe0 [size=32]
    Kernel modules: i2c-i801

01:00.0 Multimedia audio controller: Creative Labs CA0106 Soundblaster
    Subsystem: Creative Labs Device 100a
    Flags: bus master, medium devsel, latency 64, IRQ 21
    I/O ports at df20 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: CA0106
    Kernel modules: snd-ca0106

01:01.0 Communication controller: Conexant Systems, Inc. HSF 56k Data/Fax Modem
    Subsystem: Conexant Systems, Inc. Device 200f
    Flags: bus master, medium devsel, latency 64, IRQ 9
    Memory at feaf0000 (32-bit, non-prefetchable) [size=64K]
    I/O ports at df18 [size=8]
    Capabilities: <access denied>

01:08.0 Ethernet controller: Intel Corporation 82562EZ 10/100 Ethernet Controller (rev 02)
    Subsystem: Dell Device 019d
    Flags: bus master, medium devsel, latency 64, IRQ 20
    Memory at feaef000 (32-bit, non-prefetchable) [size=4K]
    I/O ports at df40 [size=64]
    Capabilities: <access denied>
    Kernel driver in use: e100
    Kernel modules: e100, eepro100
```


Looking around, I found this: [http://www.alsa-project.org/main/index.php/Matrix:Module-ca0106](http://www.alsa-project.org/main/index.php/Matrix:Module-ca0106)
Which seems to be my sound card.

I also referred to the sound card sticky in this forum. I uninstalled and reinstalled the alsa stuff like it recommends but nothing seems to happen and I haven't a clue what to do. Again, if I've left any information out, please tell me and I'll post it.

---

### Post by lilychef on 2009-05-17
This sounds like my problem... I had Sound Blaster X-Fi Extreme Audio, and there is no real viable driver for it... ALS lists it as the same chipset as the Audigy (CA 106), and that should show up in your sound settings... tell me if not, then you may have some other problem...  I managed to get 2.1 sound, but nothing more...  Apparently they are working on a better driver, but I wouldn't count on anything anytime soon....  You're probably going to have to get another sound card, but be careful to get one that's fully supported, and even then prepare for a complicated installation process... I'm new, too, and this driver swap business is for the birds....

---

### Post by lilychef on 2009-05-17
Just saw your last post...  That driver appears to already be included in the latest Ubuntu installations...  I was able to manipulate some settings with alsa mixer, etc, but was never able to get 5.1 sound...  Just pack it up, eBay it, and move on...

---

### Post by shagy on 2009-07-24
Well, about a year ago a became new to Ubuntu. Let me tell you that I upgraded to Ubuntu 9.04 and I am unable to get that sound card working with youtube videos.How I got working the sound card? First go to System/Preferences/Sound. Once there on Default Mixer Tracks select CA106 (ALSA Mixer). Then on Sound events select Audigy SE[SB0570]CA0106. Then on Music and Movies select the same. Notice that the device is in AlSA and the options above on OSS. That works with the sound from the music players but not from youtube videos. The problem seems to be that youtube requires ALSA but the sound works  only with  OSS on Sound Events and so on, as I said. My suggestion is that you download and install Ubuntu 8.04.3 LTS because the Audigy SE worked best on that release. What I mean with best? The sound on from youtube videos works. That release will enable you to upgrade to the next LTS which will come on 2010. Hope this helps.

---

### Post by markbuntu on 2009-07-25
The big problem with the audigy cards is that by default the analog/digital switch is set to digital. Open the sound mixer ( the little speaker) and uncheck the analog/digital switch. You may need to check it in preferences first to make it visible.

---

### Post by bcschmerker on 2009-07-25
> **lilychef said:**
> This sounds like my problem... I had Sound Blaster X-Fi Extreme Audio, and there is no real viable driver for it... ALS lists it as the same chipset as the Audigy (CA 106), and that should show up in your sound settings... tell me if not, then you may have some other problem...  I managed to get 2.1 sound, but nothing more...  Apparently they are working on a better driver, but I wouldn't count on anything anytime soon....  You're probably going to have to get another sound card, but be careful to get one that's fully supported, and even then prepare for a complicated installation process... I'm new, too, and this driver swap business is for the birds....In fact the [Advanced LinUX Sound Architecture Project](http://www.alsa-project.org/) has a new driver in the works, and they're working on integrating Snd-CTXFi (for the E-mu 20k1) into Kernel 2.6.31, which has me waiting for 10alpha1 Limber (Projected LinUX Kernel: 2.6.31-1-generic).  Concerning the Audigy SE, the ALSA Project is working on a new driver for the Creative Technologies CA0106 chip, due to several critical issues identified in the current version.

---

