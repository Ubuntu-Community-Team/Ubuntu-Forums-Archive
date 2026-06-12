---
title: "Very strange audio problem. Skipping when *not* under load."
date: 2008-08-28
forum: Multimedia Software
---

### Post by pib on 2008-08-28
I put together a new system a few days ago, and I've not been able to get sound working correctly.

I don't have the usual problems. My sound card was detected and modules were loaded, and no applications seem to have any trouble playing sound.

The problem is that the sound card stutters and crackles. How much it happens varies.

I noticed that flash videos tend to have ok sound (a few crackles here and there, flash using 30+% of a single CPU) until the very end of the video, then it echoes whatever the last sound was for a couple of seconds in a trailing-off, crackling sort of way.

When I play mp3s, it almost always sounds like a skipping CD, but the program playing it (I've tried several) seems to act like it's playing normally.

I imported a song into audacity, and started it playing, with the same result, sounds like a skipping CD, but I noticed that when I was moving my mouse between menus, the sound got better for a little bit.

I wrote a quick shell script:
```
while true; do sleep 0; done
```

While that is running, using about 18% of one of my cpus, the sounds stops skipping and sounds fine.

So I tried a different script:
```
while true; do echo -n; done
```

That uses up 100% of a cpu, and the audio still skips.

I'm using this motherboard's onboard sound: [http://www.biostar.com.tw/app/en-us/t-power/content.php?S_ID=351](http://www.biostar.com.tw/app/en-us/t-power/content.php?S_ID=351)

It's a Realtek ALC888S.

I've got a Socket AM2+ AMD64 Phenom 9850 Quad-core processor, 4GB of ram. Not sure what other information might  be relevant, since this seems like it could be related to more than just my audio chip.

Does anyone have any idea what could be causing this?

---

### Post by kostkon on 2008-08-28
> **pib said:**
> I put together a new system a few days ago, and I've not been able to get sound working correctly.

I don't have the usual problems. My sound card was detected and modules were loaded, and no applications seem to have any trouble playing sound.

The problem is that the sound card stutters and crackles. How much it happens varies.

I noticed that flash videos tend to have ok sound (a few crackles here and there, flash using 30+% of a single CPU) until the very end of the video, then it echoes whatever the last sound was for a couple of seconds in a trailing-off, crackling sort of way.

When I play mp3s, it almost always sounds like a skipping CD, but the program playing it (I've tried several) seems to act like it's playing normally.

I imported a song into audacity, and started it playing, with the same result, sounds like a skipping CD, but I noticed that when I was moving my mouse between menus, the sound got better for a little bit.

I wrote a quick shell script:
```
while true; do sleep 0; done
```

While that is running, using about 18% of one of my cpus, the sounds stops skipping and sounds fine.

So I tried a different script:
```
while true; do echo -n; done
```

That uses up 100% of a cpu, and the audio still skips.

I'm using this motherboard's onboard sound: [http://www.biostar.com.tw/app/en-us/t-power/content.php?S_ID=351](http://www.biostar.com.tw/app/en-us/t-power/content.php?S_ID=351)

It's a Realtek ALC888S.

I've got a Socket AM2+ AMD64 Phenom 9850 Quad-core processor, 4GB of ram. Not sure what other information might  be relevant, since this seems like it could be related to more than just my audio chip.

Does anyone have any idea what could be causing this?
It may be PulseAudio related. You can check the [this guide]("http://ubuntuforums.org/showthread.php?t=789578") for setting up PulseAudio the right way.

---

### Post by pib on 2008-08-28
I'm not using PulseAudio, so it's not that.

Looks like I'm not the first person to have this issue: [http://backports.ubuntuforums.com/showthread.php?t=881035](http://backports.ubuntuforums.com/showthread.php?t=881035)

I've got the same chip as him, lspci gives me this:
```
00:07.0 Audio device: nVidia Corporation Unknown device 0774 (rev a1)
```

He noted that it got better under load as well. Strange. Could it be a buffer/scheduler issue?

---

### Post by Crafty Kisses on 2008-08-28
Post the results of > lspci

---

### Post by pib on 2008-08-28
I just ran update-pciids, too.

```

00:00.0 RAM memory: GeForce 8800 GT 512 MCP78S [GeForce 8200] Memory Controller (rev a2)
	Subsystem: Biostar Microtech Int'l Corp Unknown device 340b
	Flags: bus master, 66MHz, fast devsel, latency 0
	Capabilities: [94] HyperTransport: #1a
	Capabilities: [60] HyperTransport: Retry Mode
	Capabilities: [44] HyperTransport: Slave or Primary Interface
	Capabilities: [d0] HyperTransport: #1c

00:01.0 ISA bridge: GeForce 8800 GT 512 Unknown device 075d (rev a2)
	Subsystem: Biostar Microtech Int'l Corp Unknown device 340b
	Flags: bus master, 66MHz, fast devsel, latency 0
	I/O ports at 2f00 [size=256]

00:01.1 SMBus: GeForce 8800 GT 512 MCP78S [GeForce 8200] SMBus (rev a1)
	Subsystem: Biostar Microtech Int'l Corp Unknown device 340b
	Flags: 66MHz, fast devsel, IRQ 10
	I/O ports at 2900 [size=64]
	I/O ports at 2d00 [size=64]
	I/O ports at 2e00 [size=64]
	Capabilities: [44] Power Management version 2

00:01.2 RAM memory: GeForce 8800 GT 512 MCP78S [GeForce 8200] Memory Controller (rev a1)
	Subsystem: Biostar Microtech Int'l Corp Unknown device 340b
	Flags: 66MHz, fast devsel

00:01.3 Co-processor: GeForce 8800 GT 512 MCP78S [GeForce 8200] Co-Processor (rev a2)
	Subsystem: Biostar Microtech Int'l Corp Unknown device 340b
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 11
	Memory at f9f80000 (32-bit, non-prefetchable) [size=512K]

00:01.4 RAM memory: GeForce 8800 GT 512 MCP78S [GeForce 8200] Memory Controller (rev a1)
	Subsystem: Biostar Microtech Int'l Corp Unknown device 340b
	Flags: 66MHz, fast devsel

00:02.0 USB Controller: GeForce 8800 GT 512 MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1) (prog-if 10 [OHCI])
	Subsystem: Biostar Microtech Int'l Corp Unknown device 340b
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
	Memory at f9f7f000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [44] Power Management version 2

00:02.1 USB Controller: GeForce 8800 GT 512 MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1) (prog-if 20 [EHCI])
	Subsystem: Biostar Microtech Int'l Corp Unknown device 340b
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
	Memory at f9f7ec00 (32-bit, non-prefetchable) [size=256]
	Capabilities: [44] Debug port
	Capabilities: [80] Power Management version 2

00:04.0 USB Controller: GeForce 8800 GT 512 MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1) (prog-if 10 [OHCI])
	Subsystem: Biostar Microtech Int'l Corp Unknown device 340b
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
	Memory at f9f7d000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [44] Power Management version 2

00:04.1 USB Controller: GeForce 8800 GT 512 MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1) (prog-if 20 [EHCI])
	Subsystem: Biostar Microtech Int'l Corp Unknown device 340b
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
	Memory at f9f7e800 (32-bit, non-prefetchable) [size=256]
	Capabilities: [44] Debug port
	Capabilities: [80] Power Management version 2

00:06.0 IDE interface: GeForce 8800 GT 512 MCP78S [GeForce 8200] IDE (rev a1) (prog-if 8a [Master SecP PriP])
	Subsystem: Biostar Microtech Int'l Corp Unknown device 340b
	Flags: bus master, 66MHz, fast devsel, latency 0
	[virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
	[virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
	I/O ports at ffa0 [size=16]
	Capabilities: [44] Power Management version 2

00:07.0 Audio device: GeForce 8800 GT 512 Unknown device 0774 (rev a1)
	Subsystem: Biostar Microtech Int'l Corp Unknown device 8213
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
	Memory at f9f78000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: [44] Power Management version 2
	Capabilities: [50] Message Signalled Interrupts: Mask+ 64bit+ Queue=0/0 Enable-
	Capabilities: [6c] HyperTransport: MSI Mapping

00:08.0 PCI bridge: GeForce 8800 GT 512 MCP78S [GeForce 8200] PCI Bridge (rev a1) (prog-if 01 [Subtractive decode])
	Flags: bus master, 66MHz, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
	Capabilities: [b8] Subsystem: Biostar Microtech Int'l Corp Unknown device 340b
	Capabilities: [8c] HyperTransport: MSI Mapping

00:09.0 IDE interface: GeForce 8800 GT 512 Unknown device 0ad0 (rev a2) (prog-if 85 [Master SecO PriO])
	Subsystem: Biostar Microtech Int'l Corp Unknown device 5409
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
	I/O ports at c080 [size=8]
	I/O ports at c000 [size=4]
	I/O ports at bc00 [size=8]
	I/O ports at b880 [size=4]
	I/O ports at b800 [size=16]
	Memory at f9f76000 (32-bit, non-prefetchable) [size=8K]
	Capabilities: [44] Power Management version 2
	Capabilities: [8c] #12 [0010]
	Capabilities: [b0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/3 Enable-
	Capabilities: [ec] HyperTransport: MSI Mapping

00:10.0 PCI bridge: GeForce 8800 GT 512 MCP78S [GeForce 8200] PCI Express Bridge (rev a1) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: fa000000-feafffff
	Prefetchable memory behind bridge: 00000000c0000000-00000000dfffffff
	Capabilities: [40] Subsystem: Biostar Microtech Int'l Corp Unknown device 340b
	Capabilities: [48] Power Management version 3
	Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable-
	Capabilities: [60] HyperTransport: MSI Mapping
	Capabilities: [80] Express Root Port (Slot+) IRQ 0

00:12.0 PCI bridge: GeForce 8800 GT 512 MCP78S [GeForce 8200] PCI Express Bridge (rev a1) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	Capabilities: [40] Subsystem: Biostar Microtech Int'l Corp Unknown device 340b
	Capabilities: [48] Power Management version 3
	Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable-
	Capabilities: [60] HyperTransport: MSI Mapping
	Capabilities: [80] Express Root Port (Slot+) IRQ 0

00:13.0 PCI bridge: GeForce 8800 GT 512 Unknown device 077a (rev a1) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	Capabilities: [40] Subsystem: Biostar Microtech Int'l Corp Unknown device 340b
	Capabilities: [48] Power Management version 3
	Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable-
	Capabilities: [60] HyperTransport: MSI Mapping
	Capabilities: [80] Express Root Port (Slot+) IRQ 0

00:14.0 PCI bridge: GeForce 8800 GT 512 Unknown device 077a (rev a1) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
	I/O behind bridge: 0000e000-0000efff
	Memory behind bridge: feb00000-febfffff
	Prefetchable memory behind bridge: 00000000f8f00000-00000000f8ffffff
	Capabilities: [40] Subsystem: Biostar Microtech Int'l Corp Unknown device 340b
	Capabilities: [48] Power Management version 3
	Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable-
	Capabilities: [60] HyperTransport: MSI Mapping
	Capabilities: [80] Express Root Port (Slot+) IRQ 0

00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] HyperTransport Configuration
	Flags: fast devsel
	Capabilities: [80] HyperTransport: Host or Secondary Interface

00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Address Map
	Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] DRAM Controller
	Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Miscellaneous Control
	Flags: fast devsel
	Capabilities: [f0] #0f [0010]

00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Link Control
	Flags: fast devsel

02:00.0 VGA compatible controller: GeForce 8800 GT 512 GeForce 8800 GS (rev a2) (prog-if 00 [VGA controller])
	Subsystem: XFX Pine Group Inc. Unknown device 2335
	Flags: bus master, fast devsel, latency 0, IRQ 19
	Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
	Memory at c0000000 (64-bit, prefetchable) [size=512M]
	Memory at fa000000 (64-bit, non-prefetchable) [size=32M]
	I/O ports at dc00 [size=128]
	[virtual] Expansion ROM at feae0000 [disabled] [size=128K]
	Capabilities: [60] Power Management version 3
	Capabilities: [68] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [78] Express Endpoint IRQ 0

05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
	Subsystem: Biostar Microtech Int'l Corp Unknown device 2307
	Flags: bus master, fast devsel, latency 0, IRQ 507
	I/O ports at e800 [size=256]
	Memory at febff000 (64-bit, non-prefetchable) [size=4K]
	Memory at f8ff0000 (64-bit, prefetchable) [size=64K]
	Expansion ROM at febc0000 [disabled] [size=128K]
	Capabilities: [40] Power Management version 3
	Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+
	Capabilities: [70] Express Endpoint IRQ 1
	Capabilities: [b0] MSI-X: Enable- Mask- TabSize=2
	Capabilities: [d0] Vital Product Data



```

Here's aplay -l in case that might help, too

```

**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

---

### Post by markbuntu on 2008-08-28
Try this thread, there is some help for ALC883 there:


[http://ubuntuforums.org/showthread.php?t=616845](http://ubuntuforums.org/showthread.php?t=616845)

---

### Post by pib on 2008-08-28
Sadly I've already tried that, with model=6stack-dig. It made no difference.

The probem isn't that sound doesn't work for me. That's the problem that most people seem to have, just no sound. 

My sound works, it just stutters and crackles.

---

### Post by markbuntu on 2008-08-28
Ok, there is a fix for that near the bottom of this guide:

[http://ubuntuforums.org/showthread.php?p=4928900](http://ubuntuforums.org/showthread.php?p=4928900)

---

### Post by pib on 2008-08-28
Sadly, that guide won't help either, since I'm not using PulseAudio.

I will try messing with my ALSA buffer size and see if that does any good.

---

### Post by markbuntu on 2008-08-28
You may have the wrong sampling rate for your card. Some cards only work at 48k and others at 44.1k. Check that when you are looking into your alsa setup. I suspect that it is most likely a buffer size or sample rate problem though.

---

### Post by pib on 2008-08-28
Cool, I'll look into that to, thanks!

---

### Post by pib on 2008-08-29
So I tried changing the buffer sizes, I tried changing the sampling rate. Still nothing.

I got some minor improvements in the skipping (and I mean minor, it was still unusably bad) with changing the buffer sizes.

Any other ideas?

---

### Post by pib on 2008-08-30
I've tried setting the nice and ionice of the process, I've tried using the realtime kernel image, I've even fiddled around with interrupts a little bit.

Still the same problem.

Has anyone actually managed to solve a similar problem?

---

### Post by AdamBlack on 2008-09-09
I am having pretty much the same problem. My motherboard has the same chipset. Ive been at this for hours and am unable to find a solution.

---

### Post by pib on 2008-09-09
Dang. I've still not found any solution, either.

I guess I'll try OSS4 and/or compiling my own kernel to see if it helps.

---

### Post by BrutishSaucer on 2008-09-10
I'm having the exact same problem.  The more load I put on the system, the better the sound gets.  When I first installed Gutsy on an HP Pavilion laptop, it had the same issue and I was able to solve it by including the acpi=off option in the Grub loader, but that doesn't work on my current desktop with Hardy.

I keep trying new things every night so I'll let you know if anything works.

---

### Post by pib on 2008-09-10
Hmm, I'll try acpi=off on mine and see if that helps. I think I also reas somewhere that noapic might help as well...

---

### Post by BrutishSaucer on 2008-09-10
I believe noacpi and acpi=off do the same thing, but the acpi=off comes equiped with more options.

---

### Post by pib on 2008-09-10
Not noacpi, noapic. They are two unrelated things.

[http://www.linuxquestions.org/questions/linux-software-2/difference-between-noapic-and-acpioff-kernel-parameters-454675/](http://www.linuxquestions.org/questions/linux-software-2/difference-between-noapic-and-acpioff-kernel-parameters-454675/)

---

### Post by pib on 2008-09-10
I tried noapic and there were some weird sata errors and it wouldn't boot.

apci=off didn't make any difference.

---

### Post by pib on 2008-09-15
I went as far as compiling a kernel with LatencyTop support. When playing a .wav file of a song with aplay, the latency was mostly non-existant.

Interestingly enough, something I hadn't noticed before (I'd never let aplay play all the way through a song before):

```
$ aplay ~/song.wav
Playing WAVE '/home/pib/song.wav' : Signed 16 bit Little Endian, Rate 44100 Hz, Stereo
underrun!!! (at least 164395.941 ms long)
underrun!!! (at least 11850.696 ms long)
underrun!!! (at least 5668.653 ms long)
underrun!!! (at least 14226.169 ms long)
```

I'm pretty sure an underrun of 164 seconds is bad...

The question is why is the data not getting to the sound card?

---

### Post by BrutishSaucer on 2008-09-21
So I put my faith in the future and upgraded from 8.04 to the test version of Intrepid 8.10.  The sound works perfectly now!  I kind of hate these solutions as there isn't the gratification of really fixing anything, but I can't complain too much.  At least I can listen to my Partridge Family mp3s now.

---

### Post by pib on 2008-09-21
Awesome, I will give that a try myself, then try and see what the difference is. It can't be the kernel, I know that for sure, since I tried building the latest kernel and that didn't fix the problem.

I'm guessing it's just a new default sound configuration. We'll see.

---

### Post by pib on 2008-09-21
Well, that did it. I'm looking around for differences, none that are obvious so far.

I'm very relieved to have it finally working, however.

---

### Post by DriverDevel on 2009-06-04
OK, you guys "solved" it, but:
Suspiciously sounded like a power management issue (some PCI bus disconnect problems or so causing crackling sound, which also happened for certain soundcards on Athlon 7 systems when manually enabling disconnect there to save ~ 15 Watts).

The idle=poll parameter would most likely have "fixed" the problem, too,
by simply staying active all the time instead of doing ACPI PM.
Other things to watch then would have been ACPI Cx handling
(cat /proc/acpi/processor/CPU0/power and such).

---

