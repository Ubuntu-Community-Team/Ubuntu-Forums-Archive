---
title: "Yet another no sound in Ibex thread"
date: 2009-02-25
forum: Multimedia Software
---

### Post by BigZee on 2009-02-25
Hi,

I like to think I have a reasonable idea of what I'm doing with GNU/Linux given that I've been using it for 10 years.

No matter what, I cannot get any sound beyond the occasional pop out of my system since I upgraded from 8.04. 

Well, that's not entirely true. There is one way to do so, run X with the nv driver instead if nvidia. I've tried various ways to identify why this is the case but I really am not able to find out what the problem is. This is a system that has given good service for a couple of years now without any problems. I can only describe this as a conflict between the nvidia driver and the alsa driver (snd-intel8x0).

Tried so far :-

1. the Ubuntu pulseaudio guide -- I really think this is a driver issue now, not a problem with pulse.
2. reinstalling alsa
3. Both of the nvidia graphics drivers available from the hardware drivers options
4. probeirq, ac97_qiurks etc.
5. plenty of google searchs

The motherboard is an Asus k8n4-e deluxe with a semperon installed. 

Any help would be appreciated. 

root@tivo2:~# uname -a
Linux tivo2 2.6.27-12-generic #1 SMP Thu Feb 5 09:26:42 UTC 2009 x86_64 GNU/Linux

root@tivo2:~# lsmod | grep snd
snd_intel8x0           43688  0 
snd_ac97_codec        133080  1 snd_intel8x0
ac97_bus               10368  1 snd_ac97_codec
snd_pcm_oss            52608  0 
snd_mixer_oss          25088  1 snd_pcm_oss
snd_pcm                99208  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy          11524  0 
snd_seq_oss            42368  0 
snd_seq_midi           15872  0 
snd_rawmidi            34176  1 snd_seq_midi
snd_seq_midi_event     16768  2 snd_seq_oss,snd_seq_midi
snd_seq                67168  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              34320  2 snd_pcm,snd_seq
snd_seq_device         16404  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    79432  10 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              16800  1 snd
snd_page_alloc         17680  2 snd_intel8x0,snd_pcm

root@tivo2:~# lspci -v
00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
	Subsystem: ASUSTeK Computer Inc. Device 815a
	Flags: bus master, 66MHz, fast devsel, latency 0
	Capabilities: [44] HyperTransport: Slave or Primary Interface
	Capabilities: [e0] HyperTransport: MSI Mapping Enable+ Fixed-

00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev a3)
	Subsystem: ASUSTeK Computer Inc. Device 815a
	Flags: bus master, 66MHz, fast devsel, latency 0

00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
	Subsystem: ASUSTeK Computer Inc. Device 815a
	Flags: 66MHz, fast devsel, IRQ 23
	I/O ports at e400 [size=32]
	I/O ports at 4c00 [size=64]
	I/O ports at 4c40 [size=64]
	Capabilities: [44] Power Management version 2
	Kernel driver in use: nForce2_smbus
	Kernel modules: i2c-nforce2

00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2) (prog-if 10)
	Subsystem: ASUSTeK Computer Inc. Device 815a
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
	Memory at d9004000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [44] Power Management version 2
	Kernel driver in use: ohci_hcd
	Kernel modules: ohci-hcd

00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3) (prog-if 20)
	Subsystem: ASUSTeK Computer Inc. Device 815a
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
	Memory at d9005000 (32-bit, non-prefetchable) [size=256]
	Capabilities: [44] Debug port: BAR=1 offset=0098
	Capabilities: [80] Power Management version 2
	Kernel driver in use: ehci_hcd
	Kernel modules: ehci-hcd

00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
	Subsystem: ASUSTeK Computer Inc. Device 812a
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
	I/O ports at dc00 [size=256]
	I/O ports at e000 [size=256]
	Memory at d9003000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [44] Power Management version 2
	Kernel driver in use: Intel ICH
	Kernel modules: snd-intel8x0

00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev f2) (prog-if 8a [Master SecP PriP])
	Subsystem: Device f043:815a
	Flags: bus master, 66MHz, fast devsel, latency 0
	[virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
	[virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
	I/O ports at f000 [size=16]
	Capabilities: [44] Power Management version 2
	Kernel driver in use: pata_amd
	Kernel modules: pata_acpi, pata_amd, ata_generic

00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3) (prog-if 85 [Master SecO PriO])
	Subsystem: ASUSTeK Computer Inc. Device 815a
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
	I/O ports at 09f0 [size=8]
	I/O ports at 0bf0 [size=4]
	I/O ports at 0970 [size=8]
	I/O ports at 0b70 [size=4]
	I/O ports at d800 [size=16]
	Memory at d9002000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [44] Power Management version 2
	Kernel driver in use: sata_nv
	Kernel modules: sata_nv, pata_acpi, ata_generic

00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3) (prog-if 85 [Master SecO PriO])
	Subsystem: ASUSTeK Computer Inc. Device 815a
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
	I/O ports at 09e0 [size=8]
	I/O ports at 0be0 [size=4]
	I/O ports at 0960 [size=8]
	I/O ports at 0b60 [size=4]
	I/O ports at c400 [size=16]
	Memory at d9001000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [44] Power Management version 2
	Kernel driver in use: sata_nv
	Kernel modules: sata_nv, pata_acpi, ata_generic

00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev a2) (prog-if 01)
	Flags: bus master, 66MHz, fast devsel, latency 0
	Bus: primary=00, secondary=05, subordinate=05, sec-latency=128
	Memory behind bridge: d4000000-d8ffffff

00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev a3)
	Subsystem: ASUSTeK Computer Inc. Device 8141
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
	Memory at d9000000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at b000 [size=8]
	Capabilities: [44] Power Management version 2
	Kernel driver in use: forcedeth
	Kernel modules: forcedeth

00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	Capabilities: [40] Power Management version 2
	Capabilities: [48] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable+
	Capabilities: [58] HyperTransport: MSI Mapping Enable+ Fixed-
	Capabilities: [80] Express Root Port (Slot+), MSI 00
	Capabilities: [100] Virtual Channel <?>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	Capabilities: [40] Power Management version 2
	Capabilities: [48] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable+
	Capabilities: [58] HyperTransport: MSI Mapping Enable+ Fixed-
	Capabilities: [80] Express Root Port (Slot+), MSI 00
	Capabilities: [100] Virtual Channel <?>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	Capabilities: [40] Power Management version 2
	Capabilities: [48] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable+
	Capabilities: [58] HyperTransport: MSI Mapping Enable+ Fixed-
	Capabilities: [80] Express Root Port (Slot+), MSI 00
	Capabilities: [100] Virtual Channel <?>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 0000a000-0000afff
	Memory behind bridge: d0000000-d3ffffff
	Prefetchable memory behind bridge: 00000000c0000000-00000000cfffffff
	Capabilities: [40] Power Management version 2
	Capabilities: [48] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable+
	Capabilities: [58] HyperTransport: MSI Mapping Enable+ Fixed-
	Capabilities: [80] Express Root Port (Slot+), MSI 00
	Capabilities: [100] Virtual Channel <?>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
	Flags: fast devsel
	Capabilities: [80] HyperTransport: Host or Secondary Interface

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
	Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
	Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
	Flags: fast devsel
	Kernel driver in use: k8temp
	Kernel modules: k8temp

01:00.0 VGA compatible controller: nVidia Corporation GeForce 8500 GT (rev a1)
	Subsystem: XFX Pine Group Inc. Device 2317
	Flags: bus master, fast devsel, latency 0, IRQ 18
	Memory at d2000000 (32-bit, non-prefetchable) [size=16M]
	Memory at c0000000 (64-bit, prefetchable) [size=256M]
	Memory at d0000000 (64-bit, non-prefetchable) [size=32M]
	I/O ports at a000 [size=128]
	[virtual] Expansion ROM at d3000000 [disabled] [size=128K]
	Capabilities: [60] Power Management version 2
	Capabilities: [68] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [78] Express Endpoint, MSI 00
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [128] Power Budgeting <?>
	Capabilities: [600] Vendor Specific Information <?>
	Kernel driver in use: nvidia
	Kernel modules: nvidiafb, nvidia

05:07.0 Multimedia video controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
	Subsystem: KWorld Computer Co. Ltd. Device 08a6
	Flags: bus master, medium devsel, latency 32, IRQ 17
	Memory at d4000000 (32-bit, non-prefetchable) [size=16M]
	Capabilities: [44] Vital Product Data <?>
	Capabilities: [4c] Power Management version 2
	Kernel driver in use: cx8800
	Kernel modules: cx8800

05:07.2 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] (rev 05)
	Subsystem: KWorld Computer Co. Ltd. Device 08a6
	Flags: bus master, medium devsel, latency 32, IRQ 17
	Memory at d5000000 (32-bit, non-prefetchable) [size=16M]
	Capabilities: [4c] Power Management version 2
	Kernel driver in use: cx88-mpeg driver manager
	Kernel modules: cx8802

05:08.0 Multimedia video controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
	Subsystem: KWorld Computer Co. Ltd. Device 08a6
	Flags: bus master, medium devsel, latency 32, IRQ 18
	Memory at d6000000 (32-bit, non-prefetchable) [size=16M]
	Capabilities: [44] Vital Product Data <?>
	Capabilities: [4c] Power Management version 2
	Kernel driver in use: cx8800
	Kernel modules: cx8800

05:08.2 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] (rev 05)
	Subsystem: KWorld Computer Co. Ltd. Device 08a6
	Flags: bus master, medium devsel, latency 32, IRQ 18
	Memory at d7000000 (32-bit, non-prefetchable) [size=16M]
	Capabilities: [4c] Power Management version 2
	Kernel driver in use: cx88-mpeg driver manager
	Kernel modules: cx8802

05:0b.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link) (prog-if 10)
	Subsystem: ASUSTeK Computer Inc. Device 808b
	Flags: bus master, medium devsel, latency 32, IRQ 16
	Memory at d8004000 (32-bit, non-prefetchable) [size=2K]
	Memory at d8000000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: [44] Power Management version 2
	Kernel driver in use: ohci1394
	Kernel modules: ohci1394

root@tivo2:~#  cat /proc/asound/cards
 0 [CK804          ]: NFORCE - NVidia CK804
                      NVidia CK804 with ALC850 at irq 20

root@tivo2:~# cat /proc/asound/modules 
 0 snd_intel8x0

---

### Post by wolfen69 on 2009-02-25
what happens if you try a live cd of ubuntu 8.10? upgrading can bork your system, and that is why i always do a fresh install. besides, a couple of hours needed to reinstall is worth it in my opinion to insure a good running system.

hopefully, someone can shed some light on this.

---

### Post by BigZee on 2009-02-25
Certainly running the live CD works. I've not properly investigated this to be honest and my firs impression (could be wrong), is that it's doing the same as I am when I can get sound to work - running NV or VGA driver instead of nvidia driver. 

I often do a full install in preference to an upgrade except that this is my mythtv box and I really don't want to have to configure it all again, especially with a database loaded with guide info and history. 

Besides, shouldn't the upgrade "just work"?

---

### Post by Yellow Pasque on 2009-02-25
The fact that you've got sound with the nv driver is a good sign. By chance, does your 8500GT have hdmi audio on it?

I hope you can get your issue diagnosed and resolved with a simple fix, but if you can't, and you're feeling impatient and adventurous, I'll suggest some more radical means of possibly fixing your sound.
Compiling ALSA from source - [http://ubuntuforums.org/showthread.php?p=6589810](http://ubuntuforums.org/showthread.php?p=6589810)
OSS4 - [https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)

---

### Post by markbuntu on 2009-02-26
The nvidia ALC 850 uses the snd-hda-intel driver. There are many options for that driver. Look in the Driver section here

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by BigZee on 2009-02-26
Sorry, I can't agree. The driver loaded (intel8x0) is correct for this hardware. I've tried blacklisting the intel8x0 driver and get nothing loaded. I've also tried to load hda_intel and although it loads, it doesn't seem to attach itself to the sound device. However, if you can give me more info to show you're right, please do so.

I've run some more tests today. This really is an odd problem.

Todays test was to run ogg123 in a remote terminal. If X is running, no sound. Stop X with /etc/init.d/gdm stop, and the sound can be heard. Restart X, and the sound goes out again. This also reinforces the idea that alsa is correctly configured and is working. In fact, I can even get ogg123 to use the pulse device and can see the entry being played in the pulse monitoring software. 

So, this comes back to pulse audio I suppose. Except that if I run up X with pulse disabled, and set the sound prefs to use the alsa device, I still get no sound :-(

So, from this I guess it's not pulse being wrong after all. Is there something else in X that could be pointing the whole lot at the wrong device? I don't see how.

---

### Post by markbuntu on 2009-02-26
Try making a new user and see if sound works there. I know it sound silly but if sound works from a remote terminal then it just may be a user config problem. A lot of people have encountered this.

---

### Post by BigZee on 2009-02-26
Interesting idea Markbuntu but no go either. One thing I've probably not mentioned before is that I don't even get the drums when GDM prompts me to login. It's one of the reasons why I'm thinking that it could be an issue with X itself.

---

### Post by markbuntu on 2009-02-27
OK then, a likely culprit is the connexant device becoming the default, a video capture card perhaps?

aplay -l
or
cat /rpoc/asound/modules

will tell you the order they were loaded in. Whichever one is device 0 will become the default. For more on dealing with multiple devices go here

[http://ubuntuforums.org/showthread.php?t=922860](http://ubuntuforums.org/showthread.php?t=922860)

---

### Post by BigZee on 2009-03-01
Hi Markbuntu,

it doesn't look like anything other than the expected sound card is loaded :-

apk@tivo2:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: CK804 [NVidia CK804], device 0: Intel ICH [NVidia CK804]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CK804 [NVidia CK804], device 2: Intel ICH - IEC958 [NVidia CK804 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
apk@tivo2:~$ cat /proc/asound/modules 
 0 snd_intel8x0

---

### Post by BigZee on 2009-03-01
Hi Markbuntu,

it doesn't look like anything other than the expected sound card is loaded :-

apk@tivo2:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: CK804 [NVidia CK804], device 0: Intel ICH [NVidia CK804]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CK804 [NVidia CK804], device 2: Intel ICH - IEC958 [NVidia CK804 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
apk@tivo2:~$ cat /proc/asound/modules 
 0 snd_intel8x0

---

### Post by BigZee on 2009-03-01
I've installed 8.10 fresh to a new partition on the same machine. I've got precisly the same problem. Sound works if not using nvidia driver but doesn't if I am. Same configuration as far as I can see. Is this a problem with a newish feature of the nvidia card? Tried both the recommended vesion - 177, and the previous version - 173.

---

### Post by BigZee on 2009-03-03
If anyone has any other suggestions I would be keen to hear them?

---

### Post by BigZee on 2009-03-03
I've plugged in an old soundblaster audigy. Again, exactly the same problem. Sound works when not running with nvidia driver or X not running but no sound when running with nvidia driver. This must be an issue being caused by the nvidia driver. As someone has pointed out before, this card does have an option on it for hdmi out (via a DVI adaptor) but I'm not using this option. I know that the nvidia drivers support hdmi now so is this an issue with the graphics driver somehow taking over the sound output? Don't ask me how, I'm just thinking of ideas.

---

### Post by markbuntu on 2009-03-03
Well, there needs to be some difference somewhere between when the nvidia driver is running and when it is not. 

You might want to try the 180 driver. The first nvidia driver that actually supports HDMI is 177.78 so it may be bugs in the previous drivers creating this problem for you. There were some reports a few months ago when those drivers came out that the nvidia driver was turning off the mobo sound chip in the bios. You might want to check into that because alsa would still load the driver in that case.

---

### Post by BigZee on 2009-03-03
I think I may be a lost cause here. From what I can see on the nvnews forums, this looks like it might be a problem without a solution (yet). Seems like it needs nvidia to disable the graphics card from taking over the sound but the options not there yet. I tried the suggested option to disable hdmi audio in the EDID but it's not working. I'm really not sure how I can solve this right now :-( but if anyone has any bright ideas I'm happy to listen.

---

### Post by markbuntu on 2009-03-03
I remember some people saying that they only had to go back into the bios and turn the mobo sound back on after the driver was installed to get their sound back. You might want to try that. Anyway, numerous people seem to have solved this issue so you might want to just look through the threads here.

btw, I am not intimately familiar with these nvidia problems, I have ati.

---

### Post by BigZee on 2009-03-04
Thx for your help Markbuntu. Alas, after the research I've done on the nvnews site and some other posts I've seen here, I realise that I'm not alone and that this is probably an issue for nvidia to tackle, whether it is a fault with the driver or not. My last hope was that I could connect the spdif input on the gfx card to my mobo. However, although the mobo does have an spdif out on the back, it doesn't have an internal connection. I think that all I can do now is to wait for nvidia to do something or start rebuilding my PC.

---

### Post by BigZee on 2009-03-04
I thought it worth summarizing the conditions of the problem I have in case it helps anyone else. Not that at this time it can help you if your problem matches mine. If you have :-

1. No sound output but have gone through the usual checks and can find no problem. 
2. You're using an nvidia graphics card (not an on-board one though) and the nvidia driver
3. Through other means (such as the console or using the nv driver) can get sound to work
4. You are connecting to a TV or monitor through either a DVI to HDMI or hdmi to hdmi

You are probably suffering from the same problem as I. In that case, the problem is this. Your monitor is basically telling your graphics card that it supports audio through HDMI, even if it's not actually connected. It's all to do with the EDID check that the nvidia card is doing. I've not been able to solve this but I suggest watching the linux forums on nvnews.net. All I can say is that you're not alone. However, although it seems nvidia know of the problem, they've done nothing to rectify it yet. It seems like it needs an option along the lines of 'overrideHDMIaudio' but there's nothing yet. 

There is some hope that they will fix this though but I don't know when. You may be able to deal with this another way though. My nvidia card has an input to allow the internal SPDIF to be connected from the motherboard (or your sound card) to the graphics card. I can't do this because my motherboard doesn't have an internal spdif, just the optical and coax external ports. Connecting this up should fix the problem. However, you could be in exactly the same situation as I and not have an internal SPDIF. 

Any other alternatives depend on how far you're prepared to go (in my opinion). Unless you're prepared to wait, you will probably have to spend some money on hardware. I suspect the cheapest way will be to get a new sound card, one that has an internal spdif. 

That's pretty much it, unless of course I'm completely wrong or you have a better idea.

---

