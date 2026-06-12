---
title: "Microphone problem Ubuntu 9.10 CA0160 SB Card"
date: 2010-03-16
forum: Multimedia Software
---

### Post by DirtyComp on 2010-03-16
Hello I am Linux - Ubuntu user 1year now and its the first time i am wrighting at this forums (i am reading the forums constantly when i have a problem)

Ok i have a Soundblaster CA0160 sound card and yesterday i needed to use my mic to comunicate with some1 far away from my location. After i pluged my mic jack (at the correct location) i relised that i couldnt capture anything . Ive read dosen's of threads related to my problem and made some corections from basic staff to more advanced but no luck (things like simple input sound configures to alsa and pulse reinstalls)

need your help i am waiting for some replay , realy need to get this work
ask what ever you want about my system info and remember i am a bit noob

Here are my system info:
Ubuntu: Release 9.10(karmic)
Kernel Linux 2.6.31-20-server
GNOME 2.28.1
Hardware: Memory 2gb
Processor:AMD Athlon 64 Processor 3500+
Sound Card :CA0160 SoundBlaster live

---

### Post by DirtyComp on 2010-03-16
this is my card info [http://www.alsa-project.org/db/?f=236520579bac3cc7b6b531d633eb5708aefbb21e](http://www.alsa-project.org/db/?f=236520579bac3cc7b6b531d633eb5708aefbb21e)

---

### Post by DirtyComp on 2010-03-16
Bump!:(

---

### Post by DirtyComp on 2010-03-16
Ok also this things:
```
lspci
00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev a3)
00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3)
00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev f2)
00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev a2)
00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev a3)
00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:0c.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev 46)
01:0d.0 Multimedia audio controller: Creative Labs CA0106 Soundblaster
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller (rev 15)
03:00.0 Mass storage controller: Silicon Image, Inc. SiI 3132 Serial ATA Raid II Controller (rev 01)
05:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce 6600 GT] (rev a2)

```
```
lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 002: ID 045e:0047 Microsoft Corp. IntelliMouse Explorer 3.0
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
``````
lspci | grep -i audio
01:0d.0 Multimedia audio controller: Creative Labs CA0106 Soundblaster

```

---

### Post by DirtyComp on 2010-03-17
tt bump  sorry need help

---

### Post by smclough on 2010-03-17
I'm having a similar problem.  under the sound preferences/input option, there are only Analog Input and Analog Microphone.  There is no response from input to the mic with both options.

results of lspci -v for the CA0106

> 05:0a.0 Multimedia audio controller: Creative Labs CA0106 Soundblaster
	Subsystem: Creative Labs Device 100a
	Flags: bus master, medium devsel, latency 32, IRQ 18
	I/O ports at 8c00 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: CA0106
	Kernel modules: snd-ca0106


---

### Post by rapiscan on 2010-03-28
I have the same card running on Ubuntu 9.10, and I'm also having the same problem.  Among the many things I've tried, I have tried different hardware profiles and I tried boosting the capture input using alsamixer from the commandline, with no luck.

Any help would be appreciated.

Edit: Some additional info

lspci -v
> 

03:01.0 Multimedia audio controller: Creative Labs CA0106 Soundblaster
	Subsystem: Creative Labs Device 1001
	Flags: bus master, medium devsel, latency 64, IRQ 21
	I/O ports at ec00 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: CA0106
	Kernel modules: snd-ca0106


arecord -l

> 

**** List of CAPTURE Hardware Devices ****
card 0: CA0106 [CA0106], device 0: ca0106 [CA0106]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 1: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 2: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 3: ca0106 [CA0106]


---

### Post by rapiscan on 2010-03-30
bump...

Anyone out there have any suggestions?

---

### Post by stevenpan on 2010-05-15
I had the same problem. Try this. open Terminal and run "alsamixer". Choose the bar labelled "CAPTURE" (on the bottom). Press up arrow to increase the volume.

It works for me.

---

### Post by WingNa on 2011-01-03
After quite some googlin' around, I also got the Soundblaster SE CA0106 to work. 

Im using PulseAudio on top of ALSA, with regular stereo sound, and PULSE config set to Analog Stereo Duplex. [[Having dumped Pulse before, I now am fond of it, after learning to master it a bit. Make sure Pulse is the default audio processor in Phonon/ Sound/ MultiMedia settings. By default the Pulse proces is niced -11 down to 9, to give super sound with any app].

First make sure you can play sound from various sources like a media player.

Then to get the mic working, open up the graphic ALSA mixer and set following:

- Master volume: your choice, but not zero of course.
- Mic: close to maximum > 90%
- IEC958: MUTE (to switch to analog sound)
- Phone, LineIn, Aux : set to ZERO levels
- Analog LFE, Rear and Side: MUTE (only doing stereo for now)
- Shared Mic/LineIn = Mic_in
- Digital Source = i2s_in
- Analog Source = Mic

et voila, it works. 

Skype audio config is set to Pulse Audio everywhere, auto-level adjustment by Skype is OFF.

I use a cheap regular Trust webcam with microphone included. Connect the mic.plug to the (blue) mic.in jack of soundcard on backplane. Skype is working perfectly, with good quality sound and video. (ADSL no more that 5mbps over here :( )

If you are not sure about the connectivity of the microphone, perfect for testing the electrics is to raise in Alsa mixer the CAPTURE Feedback level (with working sound of course) until you can hear the microphone when tapping it.


This shows that in the end, it will work, after some patience.

Kubuntu 10.04 nowadays, 4Gb DualCore 2.9Mhz Intel

TODO: Somehow tell/teach ALSA to ditch the superfluous CA0106 (#2, 3, 4) entries. Also the On-Board HDA-Intel (what a misery!) is still showing up in dimmed grey, although disabled in BIOS. So still some cleaning up to do, and we will figure out how to.

---

### Post by WingNa on 2011-01-24
After recent updates in 10.04 Lucid LTS, Pulse audio was giving problems, like with the snd_pcm_dump(), snd_pcm_delay() errors, resulting in Pulse crash/restart causing Amarok, Knotify4 and Skype processes to sky-rocket in CPU. Need to killall these and restart Pulse (most automatic) to resume. Problem is definitely Pulse related in the way it uses/ controls/ feeds the ALSA driver for my CA_0106 card.
Had to play with /etc/pulse/daemon.conf settings (higher realtime prio, more (25) and bigger (25) buffers in order to get it back to working again, even with the occassional (during high load) sound stutter. At least the sound related stuff keeps alive and Pulse does not crash.

TODO: fine-tune to the level of normal uncompromised quality sound. (I know it can, and Pulse  will stay for its endless flexibility in connecting all my sound related apps)

---

