---
title: "No sound on Mythbuntu"
date: 2011-12-03
forum: Multimedia Software
---

### Post by bpoppe on 2011-12-03
I recently installed mythbuntu on an older PC I had lying around. Everything seems to be working great, I can play video in HD, but can't get any sound out of my onboard sound. I followed both guides, as well as tried several other things from google searching to no avail. My speakers are on and working - I plugged them into my phone and got sound immediately.

I did have another sound card that I blacklisted - it was for HDMI out from my video card - which is weird because it doesn't have HDMI out (RADEON HD 2600 PRO)

As far as I can tell, everything is configured and recognized, there's just no output coming from my sound card. Super frustrating!

here's my alsa output:
[http://www.alsa-project.org/db/?f=b9a9a621b8f1598c5c033e52e7fcc53a1ecfbd95](http://www.alsa-project.org/db/?f=b9a9a621b8f1598c5c033e52e7fcc53a1ecfbd95)

I'm a relative noob, but I'm pretty committed to this as I really want to drop satellite and cable and switch to OTA and Boxee. Any suggestions are greatly appreciated.

---

### Post by bluexrider on 2011-12-03
> **bpoppe said:**
> I recently installed mythbuntu on an older PC I had lying around. Everything seems to be working great, I can play video in HD, but can't get any sound out of my onboard sound. I followed both guides, as well as tried several other things from google searching to no avail. My speakers are on and working - I plugged them into my phone and got sound immediately.

I did have another sound card that I blacklisted - it was for HDMI out from my video card - which is weird because it doesn't have HDMI out (RADEON HD 2600 PRO)

As far as I can tell, everything is configured and recognized, there's just no output coming from my sound card. Super frustrating!

here's my alsa output:
[http://www.alsa-project.org/db/?f=b9...fcc53a1ecfbd95](http://www.alsa-project.org/db/?f=b9...fcc53a1ecfbd95)

I'm a relative noob, but I'm pretty committed to this as I really want to drop satellite and cable and switch to OTA and Boxee. Any suggestions are greatly appreciated.

its funny your alsa output is blank when I visit the link. I guess thats the same a NO SOUND!

do you have "configuration files" listed
when you 

sudo lshw -c sound

---

### Post by bpoppe on 2011-12-03
Ha - sorry, fixed the link.  I copied it and it must have shortened it.  You can try it now.

> do you have "configuration files" listed
when you

sudo lshw -c sound 


This is the output:

-multimedia UNCLAIMED^[[B^[[B^[[B^[[B
       description: Audio device
       product: RV630/M76 audio device [Radeon HD 2600 Series]
       vendor: ATI Technologies Inc
       physical id: 0.1
       bus info: pci@0000:01:00.1
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list
       configuration: latency=64 mingnt=8
       resources: memory:fcaec000-fcaeffff
  *-multimedia:0
       description: Multimedia audio controller
       product: SiS7012 AC'97 Sound Controller
       vendor: Silicon Integrated Systems [SiS]
       physical id: 2.7
       bus info: pci@0000:00:02.7
       version: a0
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=Intel ICH latency=64 maxlatency=11 mingnt=52
       resources: irq:18 ioport:e800(size=256) ioport:ec00(size=128)
  *-multimedia:1
       description: Multimedia video controller
       product: CX23880/1/2/3 PCI Video and Audio Decoder
       vendor: Conexant Systems, Inc.
       physical id: a
       bus info: pci@0000:00:0a.0
       version: 05
       width: 32 bits
       clock: 33MHz
       capabilities: vpd pm bus_master cap_list
       configuration: driver=cx8800 latency=64 maxlatency=55 mingnt=20
       resources: irq:18 memory:fd000000-fdffffff

---

### Post by bluexrider on 2011-12-03
This device is unclaimed because incorrect drivers are installed

RV630/M76 audio device [Radeon HD 2600 Series]


Open a terminal and type 
lspci -v | grep -A7 -i "audio"

This should output some information about your audio hardware. An example is below. 

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) 
High Definition Audio Controller (rev 02)         
Subsystem: Toshiba America Info Systems Device ff01         
Flags: bus master, fast devsel, latency 0, 
IRQ 22         Memory at dc440000 (64-bit, non-prefetchable) [size=16K]         
Capabilities: <access denied>         Kernel driver in use: HDA Intel         Kernel modules: snd-hda-intel


should you have any other issues follow the link below


This is the diag for troubleshooting sound issues 
 [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

---

### Post by bpoppe on 2011-12-04
> This device is unclaimed because incorrect drivers are installed

RV630/M76 audio device [Radeon HD 2600 Series]

This is the audio device I blacklisted.  I don't have an HDMI out, which I assume is what that's for.  
Right now, the only output I'd like to see is stereo out (I'll use a converter to RCA) from my motherboard.  

> This is the diag for troubleshooting sound issues
[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

That's the link I followed - I've done all the steps and still no sound :(

> Open a terminal and type
lspci -v | grep -A7 -i "audio"

Here's the output:
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] SiS7012 AC'97 Sound Controller (rev a0)
	Subsystem: ASUSTeK Computer Inc. Device 810d
	Flags: bus master, medium devsel, latency 64, IRQ 18
	I/O ports at e800 [size=256]
	I/O ports at ec00 [size=128]
	Capabilities: <access denied>
	Kernel driver in use: Intel ICH
	Kernel modules: snd-intel8x0
--
00:0a.0 Multimedia video controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
	Subsystem: ATI Technologies Inc ATI TV Wonder Pro
	Flags: bus master, medium devsel, latency 64, IRQ 18
	Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
	Capabilities: <access denied>
	Kernel driver in use: cx8800
	Kernel modules: cx8800

--
01:00.1 Audio device: ATI Technologies Inc RV630/M76 audio device [Radeon HD 2600 Series]
	Subsystem: VISIONTEK Device aa08
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 10
	Memory at fcaec000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel modules: snd-hda-intel

---

