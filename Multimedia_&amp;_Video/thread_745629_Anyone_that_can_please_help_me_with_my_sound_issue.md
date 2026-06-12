---
title: "Anyone that can please help me with my sound issue"
date: 2008-04-04
forum: Multimedia &amp; Video
---

### Post by joecagle77 on 2008-04-04
Im running Ubuntu 7.10

I thought I had it fixed but after restarting no sound

**_Here is my aplay -1 output_**

**** List of PLAYBACK Hardware Devices ****
card 0: V8237 [VIA 8237], device 0: VIA 8237 [VIA 8237]
  Subdevices: 4/4
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
card 0: V8237 [VIA 8237], device 1: VIA 8237 [VIA 8237]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: AudioPCI [Ensoniq AudioPCI], device 0: ES1371/1 [ES1371 DAC2/ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: AudioPCI [Ensoniq AudioPCI], device 1: ES1371/2 [ES1371 DAC1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


**_and here is my  lspci -v output_**

joe@j-pc:~$ lspci -v
00:00.0 Host bridge: VIA Technologies, Inc. VT8378 [KM400/A] Chipset Host Bridge
        Subsystem: VIA Technologies, Inc. VT8378 [KM400/A] Chipset Host Bridge
        Flags: bus master, 66MHz, medium devsel, latency 8
        Memory at e0000000 (32-bit, prefetchable) [size=128M]
        Capabilities: <access denied>

00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, medium devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        Memory behind bridge: ec000000-edffffff
        Prefetchable memory behind bridge: e8000000-ebffffff
        Capabilities: <access denied>

00:06.0 Ethernet controller: Atheros Communications, Inc. AR5212/AR5213 Multiprotocol MAC/baseband processor (rev 01)
        Subsystem: Netgear Unknown device 5e00
        Flags: bus master, medium devsel, latency 168, IRQ 18
        Memory at ee000000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>

00:07.0 Multimedia audio controller: Ensoniq ES1371 [AudioPCI-97] (rev 08)
        Subsystem: Ensoniq Creative Sound Blaster AudioPCI64V, AudioPCI128
        Flags: bus master, slow devsel, latency 32, IRQ 20
        I/O ports at e000 [size=64]
        Capabilities: <access denied>

00:0f.0 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06) (prog-if 8a [Master SecP PriP])
        Subsystem: VIA Technologies, Inc. VT82C586/B/VT82C686/A/B/VT8233/A/C/VT8235 PIPC Bus Master IDE
        Flags: bus master, medium devsel, latency 32, IRQ 16
        [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [size=8]
        [virtual] Memory at 000003f0 (type 3, non-prefetchable) [size=1]
        [virtual] Memory at 00000170 (32-bit, non-prefetchable) [size=8]
        [virtual] Memory at 00000370 (type 3, non-prefetchable) [size=1]
        I/O ports at e100 [size=16]
        Capabilities: <access denied>

00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81) (prog-if 00 [UHCI])
        Subsystem: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
        Flags: bus master, medium devsel, latency 32, IRQ 17
        I/O ports at e200 [size=32]
        Capabilities: <access denied>

00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81) (prog-if 00 [UHCI])
        Subsystem: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
        Flags: bus master, medium devsel, latency 32, IRQ 17
        I/O ports at e300 [size=32]
        Capabilities: <access denied>

00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81) (prog-if 00 [UHCI])
        Subsystem: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
        Flags: bus master, medium devsel, latency 32, IRQ 17
        I/O ports at e400 [size=32]
        Capabilities: <access denied>

00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81) (prog-if 00 [UHCI])
        Subsystem: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
        Flags: bus master, medium devsel, latency 32, IRQ 17
        I/O ports at e500 [size=32]
        Capabilities: <access denied>

00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86) (prog-if 20 [EHCI])
        Subsystem: VIA Technologies, Inc. USB 2.0
        Flags: bus master, medium devsel, latency 32, IRQ 17
        Memory at ee010000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
        Subsystem: VIA Technologies, Inc. DFI KT600-AL / Soltek SL-B9D-FGR Motherboard
        Flags: bus master, stepping, medium devsel, latency 0
        Capabilities: <access denied>

00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
        Subsystem: Micro-Star International Co., Ltd. Unknown device 7061
        Flags: medium devsel, IRQ 19
        I/O ports at e600 [size=256]
        Capabilities: <access denied>

01:00.0 VGA compatible controller: VIA Technologies, Inc. VT8378 [S3 UniChrome] Integrated Video (rev 01) (prog-if 00 [VGA])
        Subsystem: Micro-Star International Co., Ltd. MS-7061
        Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 21
        Memory at e8000000 (32-bit, prefetchable) [size=64M]
        Memory at ec000000 (32-bit, non-prefetchable) [size=16M]
        [virtual] Expansion ROM at ed000000 [disabled] [size=64K]
        Capabilities: <access denied>

---

### Post by CRISM on 2008-04-22
I just got my Ensoniq AudioPCI card working after nearly 2 weeks of trial and error. I also had no sound on my Ubuntu Gutsy Gibbon installation, and my lspci output was similar to yours. It appears that the problem is the ALSA sound driver which appears in the lspci listing as ES1371 and in other listings as snd-ens1371. My solution was to install OSS drivers on my system. Here's an outline of the steps I followed:

1) Go to [www.opensound.com](www.opensound.com)
2) Click on Download on the left side of the page. You will get a screen of logos. 
3) Click on the Open Sound System logo.
4) Select the version to download. I chose linux 2.6 (x86) (TAR). Click Submit.
5) The next screen has the download link and also a link to installation instructions. You will need to follow the instructions on page 2 carefully. In particular, I had to make sure the downloaded package was in the root (/) directory, that I then changed to that directory before issuing the commands, and that I used the sudo instruction before each command to have root privileges. 
6) On my system, I got error messages when I first tried to execute some of the commands. If you get these messages, read them carefully. They will tell you what other packages your system is missing that are needed before the installation can proceed. You will need to download and install those packages one at a time using....sudo apt-get install missing-pkg. You must substitute the name of any package listed in the error message in place of 'missing-pkg'.
7) Once all missing packages have been installed, go back and follow the installation instructions for the OSS drivers again. When successful, you should see a number of drivers being installed by name. In particular, I believe the audiopci driver is the one that works for the Ensoniq card.
8) You will have to restart after installation.

Now here's the tricky part. I still had no sound after all the above because it was somehow still using the ES1371 driver instead of my new driver. I went to the /etc/modprobe.d folder and then edited the blacklist file in that folder. At the bottom of the file, I added the line... blacklist snd-ens1371 and saved.

When I re-booted again, I got no sound during boot. But when I tried playing a .wav file, I had full stereo sound!! I still don't get sound during boot. Guess that's another problem. By the way, my lspci command now mentions OSS AudioPCI as the driver instead of ES1371.

---

