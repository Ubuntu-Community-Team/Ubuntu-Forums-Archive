---
title: "HDMI Audio not working with ASUS M3N78-EM"
date: 2009-05-03
forum: Multimedia Software
---

### Post by Spectre5 on 2009-05-03
I know this is a common question - but I've searching google and the forums for hours and hours without finding any solution that works for me!

When going through HDMI, the video is running great on my LCD TV, but the audio is not coming through at all.  If I plug a PC Speaker into the analog out, then I get the audio there - but never from the TV via HDMI.

My motherboard is the ASUS M3N78-EM with an NVidia 8300 on-board with HDMI.  The TV is a 720p 1366x768 TV (Sharp LC-19SB25U).  I'm running Xubuntu 9.04 64 bit with a AMD 5050e processor.

aplay -l and aplay -L show that the HDMI device is hw:0,3.  I've tried to run:
```

speaker-test -c2 -twav -Dplughw:0,3

```
and it runs correctly and without errors, but I just never hear any audio noise.  I've checked the BIOS and it is outputting HDMI Audio (and I have the latest bios).  I've checked the TV volume - it is up PLENTY loud...

I have no idea what to do!  Most people that have the HDMI problems at least hear something when running a speaker-test, but I get nothing!

Any help?  Let me know of any outputs you want to see to help diagnose the problems...

As always, thanks for any help!


EDIT:  I guess I should also add that I've also gone into the alsa-mixer and turned on all options/controls, un-muted everything, set the volume up on everything, and turned all of the iec958 switches on.

EDIT:  Added that optical is not working either per Rekoil's post #6, though I have not tried it myself.  This problem is also on Ubuntu and the tag should probably be [ALL] instead of just [xubuntu], but I'm not sure how to change it now...or if it can be changed now.

---

### Post by Spectre5 on 2009-05-03
To make sure the TV was able to handle HDMI audio (I don't know why it wouldn't be able to), I plugged a DVD player into the TV and played the DVD over HDMI video+audio and it worked flawlessly...so I know the TV is not the problem here...

---

### Post by Spectre5 on 2009-05-04
Any ideas???  I've tried everything...I've also updated to the 19 ALSA drivers and the issue remains...I NEVER get audio from HDMI (but I do get it from the analog).

aplay -l
```

**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC1200 Digital [ALC1200 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

aplay -L
```

default:CARD=NVidia
    HDA NVidia, ALC1200 Analog
    Default Audio Device
front:CARD=NVidia,DEV=0
    HDA NVidia, ALC1200 Analog
    Front speakers
surround40:CARD=NVidia,DEV=0
    HDA NVidia, ALC1200 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=NVidia,DEV=0
    HDA NVidia, ALC1200 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=NVidia,DEV=0
    HDA NVidia, ALC1200 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=NVidia,DEV=0
    HDA NVidia, ALC1200 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=NVidia,DEV=0
    HDA NVidia, ALC1200 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=NVidia,DEV=0
    HDA NVidia, ALC1200 Digital
    IEC958 (S/PDIF) Digital Audio Output
hdmi:CARD=NVidia,DEV=0
    HDA NVidia, NVIDIA HDMI
    HDMI Audio Output
null
    Discard all samples (playback) or generate zero samples (capture)

```

lspci -v
(Not that it shows NVidia 8200 but the motherboard advertises an 8300 (I'm looking at the specs/manual right now...is there a reason for this or should I call up ASUS and ask them?)
EDIT:  err...I guess it does say 8300 for the VGA controller (second from bottom) which would be the video card portion of it, so nevermind!
```

00:00.0 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a2)
	Subsystem: ASUSTeK Computer Inc. Device 82f2
	Flags: bus master, 66MHz, fast devsel, latency 0
	Capabilities: <access denied>

00:01.0 ISA bridge: nVidia Corporation MCP78S [GeForce 8200] LPC Bridge (rev a2)
	Subsystem: ASUSTeK Computer Inc. Device 82f2
	Flags: bus master, 66MHz, fast devsel, latency 0
	I/O ports at 0900 [size=256]

00:01.1 SMBus: nVidia Corporation MCP78S [GeForce 8200] SMBus (rev a1)
	Subsystem: ASUSTeK Computer Inc. Device 82f2
	Flags: 66MHz, fast devsel, IRQ 15
	I/O ports at 0e00 [size=64]
	I/O ports at 0600 [size=64]
	I/O ports at 0700 [size=64]
	Capabilities: <access denied>

00:01.2 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a1)
	Subsystem: ASUSTeK Computer Inc. Device 82f2
	Flags: 66MHz, fast devsel

00:01.3 Co-processor: nVidia Corporation MCP78S [GeForce 8200] Co-Processor (rev a2)
	Subsystem: ASUSTeK Computer Inc. Device 82f2
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 11
	Memory at fcf80000 (32-bit, non-prefetchable) [size=512K]

00:01.4 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a1)
	Subsystem: ASUSTeK Computer Inc. Device 82f2
	Flags: 66MHz, fast devsel

00:02.0 USB Controller: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1) (prog-if 10)
	Subsystem: ASUSTeK Computer Inc. Device 82f2
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
	Memory at fcf7e000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: ohci_hcd

00:02.1 USB Controller: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1) (prog-if 20)
	Subsystem: ASUSTeK Computer Inc. Device 82f2
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
	Memory at fcf7fc00 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:04.0 USB Controller: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1) (prog-if 10)
	Subsystem: ASUSTeK Computer Inc. Device 82f2
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
	Memory at fcf7d000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: ohci_hcd

00:04.1 USB Controller: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1) (prog-if 20)
	Subsystem: ASUSTeK Computer Inc. Device 82f2
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
	Memory at fcf7f800 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:06.0 IDE interface: nVidia Corporation MCP78S [GeForce 8200] IDE (rev a1) (prog-if 8a [Master SecP PriP])
	Subsystem: ASUSTeK Computer Inc. (Wrong ID) Device 82f2
	Flags: bus master, 66MHz, fast devsel, latency 0
	[virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
	[virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
	I/O ports at ffa0 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: pata_amd

00:07.0 Audio device: nVidia Corporation MCP78S [GeForce 8200] High Definition Audio (rev a1)
	Subsystem: ASUSTeK Computer Inc. Device 82fe
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
	Memory at fcf78000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:08.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1) (prog-if 01)
	Flags: bus master, 66MHz, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
	Capabilities: <access denied>

00:09.0 IDE interface: nVidia Corporation MCP78S [GeForce 8200] SATA Controller (non-AHCI mode) (rev a2) (prog-if 85 [Master SecO PriO])
	Subsystem: ASUSTeK Computer Inc. Device 82f2
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 2300
	I/O ports at d480 [size=8]
	I/O ports at d400 [size=4]
	I/O ports at d080 [size=8]
	I/O ports at d000 [size=4]
	I/O ports at cc00 [size=16]
	Memory at fcf76000 (32-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>
	Kernel driver in use: ahci

00:0a.0 Ethernet controller: nVidia Corporation MCP78S [GeForce 8200] Ethernet (rev a2)
	Subsystem: ASUSTeK Computer Inc. Device 82f2
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 2299
	Memory at fcf7c000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at c880 [size=8]
	Memory at fcf7f400 (32-bit, non-prefetchable) [size=256]
	Memory at fcf7f000 (32-bit, non-prefetchable) [size=16]
	Capabilities: <access denied>
	Kernel driver in use: forcedeth
	Kernel modules: forcedeth

00:0b.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Express Bridge (rev a1)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 0000e000-0000efff
	Memory behind bridge: fd000000-feafffff
	Prefetchable memory behind bridge: 00000000f0000000-00000000fbffffff
	Capabilities: <access denied>
	Kernel modules: shpchp

00:10.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Express Bridge (rev a1)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:12.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Express Bridge (rev a1)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:13.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
	Memory behind bridge: feb00000-febfffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
	Flags: fast devsel
	Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
	Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
	Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
	Flags: fast devsel
	Capabilities: <access denied>
	Kernel driver in use: k8temp
	Kernel modules: k8temp

02:00.0 VGA compatible controller: nVidia Corporation GeForce 8300 (rev a2)
	Subsystem: ASUSTeK Computer Inc. Device 82f2
	Flags: bus master, fast devsel, latency 0, IRQ 21
	Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
	Memory at f0000000 (64-bit, prefetchable) [size=128M]
	Memory at fa000000 (64-bit, prefetchable) [size=32M]
	I/O ports at ec00 [size=128]
	[virtual] Expansion ROM at feae0000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: nvidia
	Kernel modules: nvidia, nvidiafb

05:00.0 FireWire (IEEE 1394): JMicron Technologies, Inc. IEEE 1394 Host Controller (prog-if 10)
	Subsystem: ASUSTeK Computer Inc. Device 8313
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at febff800 (32-bit, non-prefetchable) [size=2K]
	Memory at febff400 (32-bit, non-prefetchable) [size=128]
	Memory at febff000 (32-bit, non-prefetchable) [size=128]
	Memory at febfec00 (32-bit, non-prefetchable) [size=128]
	Capabilities: <access denied>
	Kernel driver in use: ohci1394
	Kernel modules: firewire-ohci, ohci1394

```

---

### Post by Spectre5 on 2009-05-04
Result from speaker-test:

speaker-test -c2 -twav -Dplughw:0,3
(runs with no errors - but I hear no audio.  As I've said, the TV volume is up almost all the way)
```


speaker-test 1.0.19

Playback device is plughw:0,3
Stream parameters are 48000Hz, S16_LE, 2 channels
WAV file(s)
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 64 to 16384
Period size range from 32 to 8192
Using max buffer size 16384
Periods = 4
was set period_size = 4096
was set buffer_size = 16384
 0 - Front Left
 1 - Front Right
...
...
...

```

I've also tried variants such as
speaker-test -c2 -twav -Dhdmi:CARD=NVidia,DEV=0
speaker-test -c2 -twav -Dplughw:0,1
and many others, but I get the same result - a successful test but without any sound!

I've tried all of the "fixes" I could find with /etc/asound.conf and alsamixer, I've updated alsa as I mentioned above...

I've seen most of the common threads about this issue - I'm getting no where though!

Any ideas????

EDIT: And no, pulseaudio is NOT installed...

---

### Post by Spectre5 on 2009-05-04
A little more information that might help someone??? Anyone?

```

$ cat /proc/asound/cards
 0 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xfcf78000 irq 20

```

```

$ cat /proc/asound/modules 
 0 snd_hda_intel

```

```

$ cat /proc/asound/card0/codec#* | grep -i codec
Codec: Realtek ALC1200
Codec: Nvidia MCP78 HDMI

```

```

$ cat /etc/modprobe.d/alsa-base.conf
# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from beeing loaded as first soundcard
options snd-pcsp index=-2

```

---

### Post by Rekoil on 2009-05-05
I am in the same boat as you (except Ubuntu), Asus M3N78-EM motherboard with an AMD 4850e processor, would love to get optical and HDMI audio working. This is the perfect motherboard for an HTPC if we can get the audio working properly.

I'm running jaunty on it, fully updated AND completely fresh install (literally finished installing 10 minutes ago), only analogue audio works properly. Latest BIOS is installed. Glad to provide any information on top of what Spectre5 has already provided.

Please devs, I'm forced to run Windows on my HTPC, feel my pain!

@Spectre5,
Feel free to change the distribution for this topic to All if you can. And maybe clarify that it's not just HDMI audio, but optical as well.

By the way, are there any other motherboards featuring the ALC1200 codec? To my knowledge this is a fairly new codec right?

---

### Post by Spectre5 on 2009-05-05
> **Rekoil said:**
> I am in the same boat as you (except Ubuntu), Asus M3N78-EM motherboard with an AMD 4850e processor, would love to get optical and HDMI audio working. This is the perfect motherboard for an HTPC if we can get the audio working properly.

I'm running jaunty on it, fully updated AND completely fresh install (literally finished installing 10 minutes ago), only analogue audio works properly. Latest BIOS is installed. Glad to provide any information on top of what Spectre5 has already provided.

Please devs, I'm forced to run Windows on my HTPC, feel my pain!

@Spectre5,
Feel free to change the distribution for this topic to All if you can. And maybe clarify that it's not just HDMI audio, but optical as well.

By the way, are there any other motherboards featuring the ALC1200 codec? To my knowledge this is a fairly new codec right?

I'm glad to find someone else feeling the pain like me!! Haha...someone to share the suffering with (sorry though!). Anyways, mine was also a nice fresh install of Xubuntu 9.04.  Make sure you've gone into the bios and checked that HDMI is turned on (chipset, south bridge, options there).  I've tried it with internal only, external only, and both interal+external codecs.

Here are a few similar threads.  Some posts have had success (not me):
[http://www.nvnews.net/vbulletin/showpost.php?p=1895025&postcount=85](http://www.nvnews.net/vbulletin/showpost.php?p=1895025&postcount=85)
[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1140776](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1140776)
[http://ubuntuforums.org/showthread.php?p=7152783#post7152783](http://ubuntuforums.org/showthread.php?p=7152783#post7152783)

These solutions don't work for me - I may try Ubuntu instead of Xubuntu and then try these solutions again - let me know if any of these work.  Lets have some fun and figure this out...


ALC1200 is pretty new, I believe.

Per this thread, post 1 (but it didn't work for me):
<http://ubuntuforums.org/showthread.php?t=843012>
> 
ALC1200
If you have an ALC 1200 sound chip (ASUS P5QL-EM mobo) you need ALSA
1.0.17 or 1.0.18 or 1.0.19 which there is a link to below. Upgrade and
add the following line to the end of the /etc/modprobe.d/alsa-base file:

Code:
options snd-hda-intel probe_mask=1




EDIT:  Not sure how to change the topic to ALL instead of xubuntu...

---

### Post by Rekoil on 2009-05-06
I can report HDMI success following tips from [http://ubuntuforums.org/showthread.php?p=7152783#post7152783](http://ubuntuforums.org/showthread.php?p=7152783#post7152783) and unmuting switches as suggested in [http://www.nvnews.net/vbulletin/showpost.php?p=1895025&postcount=85](http://www.nvnews.net/vbulletin/showpost.php?p=1895025&postcount=85)

However I can't make any digital audio work. Only analogue passed to the TV, no SPDIF optical output. Might try and change some BIOS settings (read something about only internal SPDIF or something).

---

### Post by Rekoil on 2009-05-06
Oh and to change to All distributions you click edit on first post, then click "Go Advanced" below the text area.

There seems to have been some ALC1200 related changes between 1.0.19 and 1.0.20, specifically mentioned is digital outputs, HDMI and SPDIF. Might be worth taking a look at.

[quote="ALSA 1.0.20 changelog"]ALSA: enable concurrent digital outputs for ALC1200
HDMI/SPDIF outputs for ASUS M3A-H/HDMI with ALC1200 codec.[/quote]

---

### Post by Spectre5 on 2009-05-06
> **Rekoil said:**
> Oh and to change to All distributions you click edit on first post, then click "Go Advanced" below the text area.

There seems to have been some ALC1200 related changes between 1.0.19 and 1.0.20, specifically mentioned is digital outputs, HDMI and SPDIF. Might be worth taking a look at.

hm....I went to "advanced" on the first post, but I don't see how I can change the xubuntu tag to all.  I also changed to add in optical sound on the title of the thread, but it only changed it for the first post, not the entire thing.

Anyways, which version of alsa are you running, the 1.0.18rc that comes with ubuntu 9.04 or did you upgrade to 19 - or even 20?

---

### Post by Spectre5 on 2009-05-06
> **Rekoil said:**
> I can report HDMI success following tips from [http://ubuntuforums.org/showthread.php?p=7152783#post7152783](http://ubuntuforums.org/showthread.php?p=7152783#post7152783) and unmuting switches as suggested in [http://www.nvnews.net/vbulletin/showpost.php?p=1895025&postcount=85](http://www.nvnews.net/vbulletin/showpost.php?p=1895025&postcount=85)

However I can't make any digital audio work. Only analogue passed to the TV, no SPDIF optical output. Might try and change some BIOS settings (read something about only internal SPDIF or something).

That's great that you go that working!  I tried both of those threads and combinations....but without success.  I don't know what could be different between them from xubuntu to ubuntu, but I think I'll try installing ubuntu and testing it out later tonight or tomorrow.

---

### Post by Rekoil on 2009-05-06
I'm running the version shipping with Jaunty, compiling 1.0.20 now, will let you know how it goes.

I don't see how Xubuntu/Ubuntu would make a difference, it's just a different shell with the same Audio frameworks...

Update:
YES! Success! Digital audio through the optical SPDIF is a go! :D Thanks for helping me Spectre5, good luck making yours work!

Updating to 1.0.20 and activating some switches in the audio config did the trick for anyone with similar problems.

---

### Post by Spectre5 on 2009-05-06
Great - I'll give it another go in the next few days and post my results back as well.

I'll try Xubuntu again with a fresh install...then if it doesn't work, I'll try the same thing on a fresh Ubuntu install and see what that does.

I don't know why xubuntu vs ubuntu would make a difference either - it definitely shouldn't.

---

### Post by Spectre5 on 2009-05-06
FYI - if you want both analog and digital output, this has good information on setting up both (about 3/4 or so down the page):

<http://www.mythtv.org/wiki/Configuring_Digital_Sound>

---

### Post by Rekoil on 2009-05-06
Thanks, but both are working for me now, seems all that was needed was ALSA 1.0.20. Try it! I can post some instructions if you need it.

---

### Post by Spectre5 on 2009-05-06
I think I could do it - but post some instructions anyways...just in case (and for other users).

Thanks.

---

### Post by Rekoil on 2009-05-06
Steps for installing ALSA 1.0.20 from source.
0. Open a terminal and enter the following commands
```
sudo -s
mkdir /usr/src/alsa
cd /usr/src/alsa/
```
1. Downloading and extracting the source
```
wget ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.20.tar.bz2
wget ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.20.tar.bz2
wget ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.20.tar.bz2
wget ftp://ftp.alsa-project.org/pub/plugins/alsa-plugins-1.0.20.tar.bz2
tar xjvvfp alsa-driver-1.0.20.tar.bz2
tar xjvvfp alsa-lib-1.0.20.tar.bz2
tar xjvvfp alsa-utils-1.0.20.tar.bz2
tar xjvvfp alsa-plugins-1.0.20.tar.bz2
```
2. Preparing your system for compilation
```
apt-get build-dep alsa-driver alsa-lib alsa-utils alsa-plugins
```
3. Compiling alsa-X (repeat for each package)
```
cd alsa-X-1.0.20/
./configure
make
make install
```
4. Reboot
5. Right click on the volume icon and click on open volume settings, click advanced and enable the switches (forgot what they were called, windows disk is plugged in and its 11pm).
6. Once you've followed these steps you should be able to select the entry in Sound preferences for digital audio and you'll have sound coming through the optical SPDIF. If you're not using HDMI it may already be coming out of it (mine defaulted to HDMI as my HDMI cable was plugged in).

Hope this helps. Good luck!

---

### Post by Spectre5 on 2009-05-06
Even with 1.0.20 alsa, I'm getting getting any luck with a fresh install of xubuntu.

Do you have anything in your /etc/asound.conf (or ~/.asoundrc) file?  I tried it with several things in the file and with nothing.  I've enabled the iec958 switches (I even enabled EVERYTHING that I could and put the volumes up high for everything and un-muted them all).  I'm going to try ubuntu a little later and see if that makes any difference (I don't know how/why it would...).

Also, do you still have external+internal codecs on?  Do you have the output from the bios going to HDMI or SPDIF?

I actually want HDMI, not optical, since I'll just play the sound through the TV for the moment...

Thanks!

EDIT:  And thanks for the alsa 1.0.20 instructions, they were quick and easy and saved me the time of tracking it down myself.

Also, are you using a 64 bit version of ubuntu 9.04 or 32 bit?

---

### Post by Spectre5 on 2009-05-07
Well...as expected, Ubuntu didn't work any better than Xubuntu; I don't know what else to try now.  I know the hdmi cable is good and the TV (if I use this cable and the tv with a dvd player over hdmi it all works great).

Here is what I did:

1. Upgrade the bios to 0520 (was done a few days ago already)

2.  Set bios options for internal+external codecs, with HD audio and HDMI output

3.  Install a fresh version of 64 bit Ubuntu 9.04.  Updated the entire installation and updated the NVidia drivers to the latest, 180.

4.  Install Alsa 1.0.20 per the instructions given above

5.  Enable the switches for iec958 (and all others) and enable them all.  I also tried various combinations of them on and off.

6.  Set the sound preferences to all be Alsa and and mixer to be Alsa.  Then when I press the test audio button it does not work.  If I change the setting to analog and test it, then I can hear it via some headphones.  I then un-plug the headphones, turn the audio to HDMI again, but it still does not work.  TV volume is up.

7.  I then try to add several combinations of lines to my /etc/asound.conf file, but this does not work either.

8.  I un-installed pulseaudio.  Still not working.

I'm totally out of ideas...I have no clue what else to try now.  I've been searching the boards for days and I've tried all of the solutions I've seen and I followed the advice of others that have gotten hdmi audio to work with this motherboard...nothing is working for me.  I've never heard anything from the hdmi audio.

My CPU is pretty much the exact same as others as well (5050e vs 4850e), not that it should matter.

I'll keep tinkering around abit and searching other forums/solutions too...but it looks like I might have to wait a bit longer to get my HTPC setup :(

I don't understand why it won't work for me but is for others...I think I might try a 32 bit install to see if that does anything different...

---

### Post by Rekoil on 2009-05-07
No asound.conf or asoundrc files, BIOS settings (running 0503 BIOS, don't think that would make a difference) are as follows.
Internal and external codec
HD Audio (not that that matters in this case as it's only used for the front panel)
SPDIF Output (HDMI works as well though)

I'm running a 32bit version of Ubuntu. Have you tried manually selecting the HDMI output? Are you running the latest NVidia drivers? (as audio output is piped through the HDMI port on the NVidia 8300)

---

### Post by Spectre5 on 2009-05-07
> **Rekoil said:**
> No asound.conf or asoundrc files, BIOS settings (running 0503 BIOS, don't think that would make a difference) are as follows.
Internal and external codec
HD Audio (not that that matters in this case as it's only used for the front panel)
SPDIF Output (HDMI works as well though)

I'm running a 32bit version of Ubuntu. Have you tried manually selecting the HDMI output? Are you running the latest NVidia drivers? (as audio output is piped through the HDMI port on the NVidia 8300)

I tried it again last night with a 32 bit installation of ubuntu, but without success.  What exactly do you mean by manually selecting the HDMI port?  I've tried to manually specify it in the speaker-test command via "-Dplughw:0,3" and "-Dhdmi:NVidia" as well as a few others.  I've also selected the hdmi output in the sound preferences (instead of auto), etc, etc.

I do have the latest NVidia drivers (180).  These are the ones that hardware detect installs, so I'm not 100% sure that it is the absolute latest version of 180...

---

### Post by Spectre5 on 2009-05-07
Rekoil, you didn't make any changes to your xorg.conf file, did you?  Can you post it here (/etc/X11/xorg.conf)?

Also, did you update the NVidia drivers to a beta release or just the one that Ubuntu automatically installed via hardware drivers?

Thanks!

---

### Post by Rekoil on 2009-05-08
Automatically installed drivers (NVidia 180). Nope, besides disabling Force GPU Scaling and setting the resolution to 1080p@25Hz I haven't changed anything in my xorg.conf. By manually selecting HDMI I meant opening the Sound preferences and selecting the HDMI audio device.

---

### Post by Spectre5 on 2009-05-09
This is so frustrating - the fact that others can get it work on this board but it won't for me.  I've tried everything and every solution I've been able to find...every version of alsa from 1.0.18 to 1.0.20, etc, etc...I'm lost.  I guess I have to just wait for another version of alsa or nvidia drivers and hope that it will fix this...

---

### Post by Rekoil on 2009-05-09
Have you wired everything properly in your case? Is your front audio connector actually capable of HD audio? Is there anything plugged into any of the other audio outputs? Did you test the asound.conf thing? Cause that got my HDMI to work even on 1.0.18b.

Are you using the NVidia 8300 chipset or is there a secondary GPU in your setup?

---

### Post by Spectre5 on 2009-05-10
> **Rekoil said:**
> Have you wired everything properly in your case? Is your front audio connector actually capable of HD audio? Is there anything plugged into any of the other audio outputs? Did you test the asound.conf thing? Cause that got my HDMI to work even on 1.0.18b.

Are you using the NVidia 8300 chipset or is there a secondary GPU in your setup?

I don't even have the case audio plugged into the motherboard - the HDMI port is on the motherboard and I'm plugging straight into that.  I've tried it with analog speakers plugged in, but mostly I've tried it without anything plugged into any other audio port.  I've tried a number of different asound.conf files, but without success.  It is interesting that you got it to work even with the 1.0.18b alsa drivers...I really don't know what else could possibly be different between ours.  Maybe I'll try another 32 bit install (the one time I tried it, it did seem like a weird install as some things weren't working totally right).  And with a 32 bit install, our systems would be practically identical!

Thanks for the suggestions though!

---

### Post by Spectre5 on 2009-05-10
Another 32 bit install (of Xubuntu this time) still didn't work!

---

### Post by Rekoil on 2009-05-12
> **Spectre5 said:**
> I don't even have the case audio plugged into the motherboard - the HDMI port is on the motherboard and I'm plugging straight into that.  I've tried it with analog speakers plugged in, but mostly I've tried it without anything plugged into any other audio port.  I've tried a number of different asound.conf files, but without success.  It is interesting that you got it to work even with the 1.0.18b alsa drivers...I really don't know what else could possibly be different between ours.  Maybe I'll try another 32 bit install (the one time I tried it, it did seem like a weird install as some things weren't working totally right).  And with a 32 bit install, our systems would be practically identical!

Thanks for the suggestions though!

Can you get any audio output when using analogue speakers via the 3.5mm jack?

---

### Post by Spectre5 on 2009-05-13
> **Rekoil said:**
> Can you get any audio output when using analogue speakers via the 3.5mm jack?

Ya, I get analog audio out if I us -Dplughw:0,0 for the speaker-test.  I don't know about optical/digital since I have not way of testing it (it would be -Dplughw:0,1).  Then, of course, HDMI does not work, which is -Dplughw:0,3.

---

### Post by Rekoil on 2009-05-13
And you definitely know those commands should work? Because I used the ubuntu sound preferences to test my sound.

---

### Post by Wyv on 2009-05-13
'Ello,

Upgrading to ALSA 1 summat 20, unmuting the IEC958 switch in Alsamixer and also manually adding the line

```
load-module module-alsa-sink device=hw:0,1 
```

to /etc/pulse/default.pa (which brings the device into PulseAudio, something it doesn't do automatically.)

Then I set the new sink to be default in PA's volume control.

I have an Asus M3N-HD HDMI AM2 Motherboard - Nforce 750a - with the ACL1200 I believe.

```
 aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC1200 Digital [ALC1200 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

I have the BIOS at the default settings for related things. The only stuff outside of the standard build I've gone for is ALSA, thanks to the previous instructions.

```
cat /proc/asound/version 
Advanced Linux Sound Architecture Driver Version 1.0.20.
Compiled on May 13 2009 for kernel 2.6.28-11-generic (SMP).
```


Newbie signing off...

---

### Post by Spectre5 on 2009-05-13
> **Rekoil said:**
> And you definitely know those commands should work? Because I used the ubuntu sound preferences to test my sound.

I tried using the Ubuntu sound preference when I installed Ubuntu (This option isn't available on Xubuntu though).  I tried both on Ubuntu - neither worked.

---

### Post by Spectre5 on 2009-05-13
To Wyv, I don't even have PulseAudio installed right now, but other than that - I've done the same (upgraded to 1.0.20 ALSA).

However...I did notice the following.../proc/asound/version reports that the version is 1.0.18, but I installed 1.0.20 by compiling it myself per Rekoil's directions before.  It installed without any errors and as you can see, speaker-test reports that version 1.0.20 is installed.  Very weird problem...


```

$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.18.
Compiled on May 10 2009 for kernel 2.6.28-11-generic (SMP).

```

```

$ speaker-test -c2 -twav -Dplughw:0,3

speaker-test 1.0.20

Playback device is plughw:0,3
Stream parameters are 48000Hz, S16_LE, 2 channels
WAV file(s)
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 64 to 16384
Period size range from 32 to 8192
Using max buffer size 16384
Periods = 4
was set period_size = 4096
was set buffer_size = 16384
 0 - Front Left
 1 - Front Right

```

---

### Post by Wyv on 2009-05-14
Oddness! I guess something didn't take?

I only have PCM working over SPDIF at the moment so it's not like I have digital passthrough yet which is the next step.

Also I took these steps after a clean install with a backed up homedir.

I'll try to find an HDMI cable to see if this is the right direction for getting that going too.

---

### Post by Spectre5 on 2009-05-14
I've done the ALSA upgrade on a fresh install too.  In fact, I've done it on many fresh installs (64 and 32 bit installations of Ubuntu and Xubuntu, some of them several times).  If you can find an HDMI cable, please let me know if it works!

I want to try hooking up my computer to another HDMI TV/monitor, but I don't have one available (could tell me if it was the TV or not...).

I may try the ALSA upgrade again with a fresh 64 bit Ubuntu install tonight and see if /proc/asound/version reports correctly with it...

---

### Post by Spectre5 on 2009-05-15
So I did another fresh install of 64 bit Ubuntu.  I installed ALSA slightly different than before (via [http://monespaceperso.org/blog-en/2009/05/09/upgrade-alsa-1020-on-ubuntu-jaunty-904/](http://monespaceperso.org/blog-en/2009/05/09/upgrade-alsa-1020-on-ubuntu-jaunty-904/)) but also configuring with the "--with-sequencer=yes" option.

This time, /cat/proc/version does report 1.0.20 as well as speaker-test.  So that is good news.  The bad news is that I still don't get any HDMI audio.  I've unmuted all of the devices, made sure the volume was up, etc without success.  I tried adding that line to the pulseaudio file (a few posts up) but that did not work either (of course I made device be hw:0,3 instead of hw:0,1 since HDMI is my device 3).  I then uninstalled pulseaudio, again this got me no where.

I tried some of the standard default options in /etc/asound.conf, but this got me no where either.

Still searching...

EDIT:
I also meant to include this...when configuring the alsa-driver, I recieved this message...not sure if it would affect anything as it continued to configure and never reported an error:
```

...(more)...
checking for kernel linux/version.h... yes
checking for kernel linux/autoconf.h... yes
checking for kernel version... 2.6.28-11-generic
checking for GCC version... ./configure: eval: line 5233: syntax error near unexpected token `)'
./configure: eval: line 5233: `my_compiler_version=4.3.3-5ubuntu4)'
Kernel compiler:  Used compiler: gcc (Ubuntu 4.3.3-5ubuntu4) 4.3.3

*** NO PREDEFINED KERNEL COMPILER IS DETECTED
*** Assuming the same compiler is used with the current system compiler.

*** Please make sure that the same compiler version was used for building kernel.

checking for built-in ALSA... no
checking for existing ALSA module... yes
checking for Red Hat kernel... auto
...(more)...

```

---

### Post by Wyv on 2009-05-16
I bought an HDMI cable, using device 0:3 and aplay test worked.

I'm currently using my onboard graphics until the discrete card arrives; when that does I'll have to cable in SPDIF to it I believe in order to get audio down the HDMI path. There are jumpers on the mobo for that (or I might just use the onboard SPDIF direct to a receiver.)

Since I know that that device works I can work on getting bitstream signals instead of PCM sent down it.

Edit: PS: opened an AC3 movie in SMPlayer, selected preferences - audio

Chose SPDIF passthrough
Chose the SPDIF output from the list of available drivers (output driver alsa 0,1)

Then my receiver picked up the Dolby Digital stream as full 5.1 and it worked fine.

---

### Post by Rekoil on 2009-05-16
Using XBMC I got digital audio (both DTS and AC3) via optical using ALSA 1.0.20 with no extra configuration necessary.

---

### Post by ErwinVdl on 2009-05-19
I would like to point out that I have been going to exactly all the pains mentioned in this thread as well, to no avail.
What bugs me the most is that I was able to get SPDIF sound working on 8.10 through upgrading Also to 1.19. However, after having installed 9.04, with all the efforts mentioned in this thread and others, I now get perfect VDPAU-accelerated Video, without any sound at all.
I am now on the brink of shelling out for a copy of Vista...

---

### Post by Rekoil on 2009-05-19
I know what you mean, I'm running Vista on it at the moment because I can't for the love of nice things get VDPAU-accelerated video working (1080p lags to the point of being completely unwatchable!). Think you have any idea exactly what did it in your case? Are you using the on board video card of the motherboard?

---

### Post by ErwinVdl on 2009-05-19
Appearantly all it took was a fresh install of the Mint-flavor of 9.04 (version 7 RC) and enabling the NVIDIA-180 driver. Planet Earth @1080p with 4.5% CPU usage. I now have a perfect setup for remastered movies up to the 1920's. Sound is way overrated ;-)

---

### Post by Rekoil on 2009-05-19
Planet Earth 1080p does not play using VDPAU for me (have Nvidia 180 enabled in Linux Mint) and The Bourne Ultimatum at 1080p is still unwatchable :(

Did you say you had the ASUS M3N78-EM board?

---

### Post by Spectre5 on 2009-05-20
Ya, do you have the same motherboard ErwinVdl?

Maybe I should try Linux Mint too...


EDIT:
And are you running 32 bit or 64 bit Linux Mint?

EDIT 2:
Nevermind...looks like there is only 32 bit version of Linux Mint 7...64 bit version of V6 exist though

---

### Post by ErwinVdl on 2009-05-20
I indeed have the same evil MB. 32bit Mint.

---

### Post by Spectre5 on 2009-05-20
ErwinVdl, have you tried audio over HDMI?  I wish I had optical/digital audio to try (and use), but I only plan to use my TV speakers at the moment via HDMI.  Analog works fine.

Also, just out of curiosity, what processor do you have?


I just installed Mint 7 "Main" and upgraded to the 180 drivers, but it did not seem to do the trick either...

---

### Post by Spectre5 on 2009-05-20
What TV or monitor do each of you have?

---

### Post by Spectre5 on 2009-05-20
A friend of mine let me borrow his 64 bit Windows CD...I installed windows, but there was still no audio.  Then I updated to SP2 and now I have great, clean, loud audio in Windows (through HDMI)!  So I know HDMI audio CAN work...

So I know the motherboard can output sound...and I know the TV can receive.  Why won't Linux work?!?  This is one of the first times (if not the first time) that I've ever been able to say that something works better in Windows... :(

I really, really don't want to have a Windows HTPC though...

---

### Post by arkania on 2009-05-21
I'm going through the exact same aggravation myself, same motherboard.

Interestingly, there's a Internet box called the Neuros Link which uses a customized version of Ubuntu and the same motherboard AND has HDMI output.  Apparently there is a script on the desktop that switches the HDMI audio on.  Love to know how they do that.

Look here:

[http://www.deviceguru.com/first-impressions-of-the-neuros-link/](http://www.deviceguru.com/first-impressions-of-the-neuros-link/)

---

### Post by arkania on 2009-05-21
Wait, ignore that folks.  It's for the M3A78-EM, not the N.  My bad. :)

---

### Post by Rekoil on 2009-05-21
Haha, yeah I thought the board looked a bit different, thought it may just have been another revision or something. Well HDMI audio can be made to work following my steps earlier in this thread (page 2 or 3 i believe).

I have a Samsung LE40A656/A1F (firmware 1020.1, Amber configuration) as the monitor.

ErwinVdl, are you using the built in card or do you have a discrete card plugged in (I'm assuming built in, but always best to ask seeing how I get such huge performance lags in VDPAU setups whereas you don't seem to).

---

### Post by mr_raider on 2009-05-21
Sorry to post here, but this seems the closest thread to my problem. I'm using the Asus m3n78-VM which is the same chipset.

9.04 32-bit with the default nvidia drivers.

HDMI shows up at device 0,3 in aplay.

If I set everything manual in sound preferences to HDMI, or play a test sound through device 0,3 it's fine and I get audio.

Pulse audio however will not recognize the HDMI as a valid sink, only gives me analog as an option. This means I can't select it as an output in pa device chooser.

Any ideas?

---

### Post by dirkboy on 2009-05-22
Thanks to the help of the guys in this thread and some other sources in the web I got
HDMI and SPDIF to work.

To sum up what I did:

Open a terminal and get root:
```
sudo su
```Install newest NVIDIA drivers (but uninstall all existing nvidia packages first)
```

cd /root
apt-get autoremove nvidia-*
wget http://us.download.nvidia.com/XFree86/Linux-x86/180.51/NVIDIA-Linux-x86-180.51-pkg1.run
/etc/init.d/gdm stop
sh NVIDIA-Linux-x86-180.51-pkg1.run

```Be aware, this pkg1 is the i386 driver, there's also one for 64bit.

Install pulseaudio and PulseAudio Volume controls:
```
apt-get install pulseaudio pulseaudio-utils gstreamer0.10-pulseaudio pavucontrol padevchooser
```Install the newest Alsa Driver like mentioned before in this thread:
```

mkdir /usr/src/alsa
cd /usr/src/alsa/

wget ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.20.tar.bz2
wget ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.20.tar.bz2
wget ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.20.tar.bz2
wget ftp://ftp.alsa-project.org/pub/plugins/alsa-plugins-1.0.20.tar.bz2
tar xjvvfp alsa-driver-1.0.20.tar.bz2
tar xjvvfp alsa-lib-1.0.20.tar.bz2
tar xjvvfp alsa-utils-1.0.20.tar.bz2
tar xjvvfp alsa-plugins-1.0.20.tar.bz2

apt-get build-dep alsa-driver alsa-lib alsa-utils alsa-plugins

cd alsa-driver-1.0.20/
./configure
make
make install

cd alsa-lib-1.0.20/
./configure
make
make install

cd alsa-utils-1.0.20/
./configure
make
make install

cd alsa-plugins-1.0.20/
./configure
make
make install
```**REBOOT!**

Check ALSA driver version:
```
cat /proc/asound/version 
Advanced Linux Sound Architecture Driver Version 1.0.20.
Compiled on May 13 2009 for kernel 2.6.28-11-generic (SMP).
```Check Devices:
```
 aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC1200 Digital [ALC1200 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```So you want to have Device 0,1 and 0,3 to be shown in PulseAudio and Volume Controls!
For that  add following lines at the end of **/etc/pulse/default.pa**
```
load-module module-alsa-sink device=hw:0,1
load-module module-alsa-sink device=hw:0,3
```[B]
REBOOT![/B]

Open Standard Volume Control and select Alsa Mixer. (you should already see Playback
PulseAudio devices)

[IMG]http://www.nabla.org/volume.jpg[/IMG]


Enable all switches and volume controls.
Turn on all IEC958 switches.

[IMG]http://www.nabla.org/iec958.jpg[/IMG]

Be sure that no control is muted.
Then save your settings so you don't have to do it all over again after each reboot:

```
sudo alsactl store
```Some programs still use the analogue output instead of the HDMI / SPDIF.
This has to be **changed** to HDMI / Digital!
In VLC this is done by a setting within the Program
in VLC -> Tools/Extras -> Preferences -> show ALL (bottom left) -> Audio

For HDMI output in other programs you have to **move the stream**.
Open PulseAudio Volume Control.
Start the program which you will use for playing videos.
Play a video file with sound (**THIS IS NECESSARY**)
**Only if** the audio is playing you can move the audio stream from Analog to
HDMI or SPDIF within PulseAudio Volume Control.



[IMG]http://www.nabla.org/pulseaudio.jpg[/IMG]


Hope that helps some of you :p

---

### Post by Rekoil on 2009-05-23
Nice summary, this is essentially what I have done as well. My problem now is getting VDPAU working :(

---

### Post by dirkboy on 2009-05-24
did you try using ffmpeg with mplayer?

```
apt-get install ffmpeg
```

try following

```
ffmpeg -formats | grep vdpau
```

i get an output like

```
D V D  h264_vdpau      H.264 / AVC / MPEG-4 AVC / MPEG-4 part 10 (VDPAU acceleration)
 D V DT mpeg1video_vdpau MPEG-1 video (VDPAU acceleration)
 D V DT mpegvideo_vdpau MPEG-1/2 video (VDPAU acceleration)
 D V D  vc1_vdpau       SMPTE VC-1 VDPAU
 D V D  wmv3_vdpau      Windows Media Video 9 VDPAU
```

---

### Post by Spectre5 on 2009-05-24
Thanks for the details instructions with screenshots of everything you did, hopefully it will help others!

---

### Post by pnauta on 2009-06-15
I just got it working using the thread [http://www.gossamer-threads.com/lists/mythtv/users/369044](http://www.gossamer-threads.com/lists/mythtv/users/369044) 

I just looked at your alsa-base.conf and I can't find anything like 

```
options snd-hda-intel model=6stack-dig
```

in there. After doing that and rebooting, there's (red) light at the end of the tunnel (optical cable).  I have yet to connect it to my receiver (which is 2 stories down) but at least I'm back in business.

---

### Post by Spectre5 on 2009-06-15
> **pnauta said:**
> I just got it working using the thread [http://www.gossamer-threads.com/lists/mythtv/users/369044](http://www.gossamer-threads.com/lists/mythtv/users/369044) 

I just looked at your alsa-base.conf and I can't find anything like 

```
options snd-hda-intel model=6stack-dig
```

in there. After doing that and rebooting, there's (red) light at the end of the tunnel (optical cable).  I have yet to connect it to my receiver (which is 2 stories down) but at least I'm back in business.

My posted alsa-base.conf does not have that option in it because I tried it with that option and it did not work.  So then I returned the file to its original state since the option didn't work.  You get it working with HDMI or you are just trying the optical?

---

### Post by Rekoil on 2009-11-09
Sorry for ressurecting a dead topic, I'm just curious if Spectre5 ever got it working?

---

### Post by Spectre5 on 2009-11-09
> **Rekoil said:**
> Sorry for ressurecting a dead topic, I'm just curious if Spectre5 ever got it working?

Hey Rekoil...a post from the dead!  I had tried everything I could at the time, from this thread an many others.  I eventually just decided to use the analog adapters (when using HDMI, the TV lets me select between HDMI audio or analog audio).  I got sick of trying so many different solutions and wanted to move on!  After seeing some other threads continue to progress, and with even newer alsa drivers, perhaps I would have better luck now, but I haven't tried again in months.

Sadly, I can't go back to re-tackle this problem since I no longer have a TV!  I just use my monitor to watch hulu and other internet content instead.  So when/if I get a new TV, then I'll try this again...

---

### Post by Lexje on 2010-01-13
> **Spectre5 said:**
> Hey Rekoil...a post from the dead!  I had tried everything I could at the time, from this thread an many others.  I eventually just decided to use the analog adapters (when using HDMI, the TV lets me select between HDMI audio or analog audio).  I got sick of trying so many different solutions and wanted to move on!  After seeing some other threads continue to progress, and with even newer alsa drivers, perhaps I would have better luck now, but I haven't tried again in months.

Sadly, I can't go back to re-tackle this problem since I no longer have a TV!  I just use my monitor to watch hulu and other internet content instead.  So when/if I get a new TV, then I'll try this again...

Hi Guys,

Just my 2 cts:
I've been in a similar situation. Mobo = M3N78-EM.
Using Kubuntu 0710, 0810, Ubuntu Karmic and all.
My main focus was to get LinuxMCE running, at first with 0710 as a base, now with 0810 as a base.

I can confirm I have everything running now on 0810. (Can post uname & alsa & nvidia versions later if you want)

I have been in the same boat banging my head to get my audio where I wanted it -> s/pdif out (integrated on backplate mobo outlet plate).
In the beginning I did not want to tackle HDMI sound out, as I thought this would only complicate matters.

What was the solution?
This mobo has in fact 3 ways to output digital sound.
1. Via HDMI bundled outlet.
2. Via s/pdif outlet on mobo connector backplate
3. Via s/pdif connector sitting on mobo itself.( See mobo manual Page 1-29: Digital audio connecctor (4-1 pin SPDIF_OUT))

At a point I had a new LCE-TV connected and suddenly increasing volume gave me sound over the TV-speakers -> via HDMI
From then onward, I was unable to direct it back over to my s/pdif connector on the mobo back plate.

I then, finally, tried to connect a separate s/pdif connector like this one [http://www.ncix.com/products/index.php?sku=111102044&vpn=SPDIF-OUT%2FOPT&manufacture=Asus]("http://www.ncix.com/products/index.php?sku=111102044&vpn=SPDIF-OUT%2FOPT&manufacture=Asus").
From then onward, I could either choose audio via HDMI, or audio via the separate s/pdif connector.

I was unable to direct sound to the mobo backplate s/pdif connector.
I asume with some redirection trick this must be possible though.

So I guess, Spectre, that after all you were having sound on plenty occasions, but didn't have it connected to the correct output...

Hope this helps for some people :-)

Erwin

---

### Post by Spectre5 on 2010-01-13
Hey, thanks for the info.  Glad that you have it working.  It sounds like the HDMI worked for you pretty much out of the box though, right?  I never even tried s/pdif, I ONLY tried audio+video via HDMI and was never successful.  I've heard many more success stories with s/pdif though then HDMI.

Also, there have been a number of new releases (ubuntu/alsa/etc) since I last tried, so for all I know, it might work just perfect out of the box now-a-days anyways (that'd be nice!).

---

### Post by lewiscypher on 2010-03-12
Hell Yeah... A Very Huge thanks to you OP, I have been toying with this wayyyyy tooo long and your instructions worked flawlessly...  Now to optimize for HD video :)



Appreciate you taking the time to share!

---

