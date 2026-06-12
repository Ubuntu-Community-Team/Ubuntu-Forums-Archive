---
title: "No sound since clean Karmic install"
date: 2010-02-21
forum: Multimedia Software
---

### Post by lift_test on 2010-02-21
Acer travelmate 4200, had no sound since a full install (not upgrade) of Karmic.  Sound has worked in all previous incarnations of Ubuntu.  When I try to play Audio CD I can hear a click from the speakers but only silence after that.  CD plays OK if booted in XP or Win7.
Output from aplay -l

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Output fromlspci -v
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
	Subsystem: Acer Incorporated [ALI] Device 0090
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
	Subsystem: Acer Incorporated [ALI] Device 0090
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at d0200000 (32-bit, non-prefetchable) [size=512K]
	I/O ports at 5088 [size=8]
	Memory at c0000000 (32-bit, prefetchable) [size=256M]
	Memory at d0300000 (32-bit, non-prefetchable) [size=256K]
	Capabilities: <access denied>
	Kernel driver in use: i915
	Kernel modules: i915

00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
	Subsystem: Acer Incorporated [ALI] Device 0090
	Flags: bus master, fast devsel, latency 0
	Memory at d0280000 (32-bit, non-prefetchable) [size=512K]
	Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
	Subsystem: Acer Incorporated [ALI] Device 0090
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at d0340000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel


Can anybody suggest what I can try?

---

### Post by DotNate on 2010-02-21
For some reason, whenever I install Karmic, I have to turn the volume levels up in alsamixer.  They are always way too low.  If you haven't tried that, it's a good place to start.

---

### Post by lift_test on 2010-02-23
Thanks for suggestion, Alsa wasn't loaded so loaded.  When I started it the volume was set at 100% but still no sound.

---

### Post by eminembdg on 2010-02-24
Im in the same boat as the OP. I have Nvidia ALC883 analog also and I have sound but no sound from headphones.

Been searching and trying things for over a week and still no headphone sound.....

my aplay -l

**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


Any help would be greatly appreciated

---

### Post by eminembdg on 2010-03-10
bump

(10char)

---

### Post by iClouseau88 on 2010-03-10
Take a look at my Post #12 on page 3 ofthis sub-forum:

By iClouseau88: "No sound and audio card not recognized by Karmic..."

---

### Post by eminembdg on 2010-03-10
> **iClouseau88 said:**
> Take a look at my Post #12 on page 3 ofthis sub-forum:

By iClouseau88: "No sound and audio card not recognized by Karmic..."

Thanks, I followed what you said in that topic word for word, but then I had NO sound whatsoever once I added that line to the alsa file.

Thanks anyways... still have no sound thru headphones

---

### Post by iClouseau88 on 2010-03-10
Hi eminembdg,

I was trying to respond to the original poster but somehow mistakenly replied to you.  My apology.  Anyway, you just cannot copy word for word because in general different audio devices have different driver files. What you could do first of all is to determine the audio controller and its driver file in your machine, by typing the following in a console, i.e. terminal:

$lspci -v

Then based on the result go to [www.alsa-project.org](www.alsa-project.org) to look for the manufacturer, device name and driver file.  For the rest, you need to look at a couple of sub-forums or google then adapt to your specific situation.

Good luck!

---

### Post by inobe on 2010-03-11
when i installed karmic pcm in sound properties was turned down, when i turned it up i had sound.

the same in xubuntu & kubuntu.

seems like karmic on any buntu has this.

---

### Post by garvinrick4 on 2010-03-11
This has worked for me on every install of Karmic or upgrade to.
Be sure to reboot when done to take effect and turn the sound down
so not to hurt your ears.

[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

---

### Post by eminembdg on 2010-03-11
> **iClouseau88 said:**
> Hi eminembdg,

I was trying to respond to the original poster but somehow mistakenly replied to you.  My apology.  Anyway, you just cannot copy word for word because in general different audio devices have different driver files. What you could do first of all is to determine the audio controller and its driver file in your machine, by typing the following in a console, i.e. terminal:

$lspci -v

Then based on the result go to [www.alsa-project.org](www.alsa-project.org) to look for the manufacturer, device name and driver file.  For the rest, you need to look at a couple of sub-forums or google then adapt to your specific situation.

Good luck!


Ok, thanks. I did do lspci -v and here is the readout for my sound device:
 
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
	Subsystem: Giga-byte Technology Device a002
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
	Memory at ec000000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel
I can't seem to find anything with these names and all. But thanks for the help. I'll deal with no sound from headphones for now.

---

### Post by eminembdg on 2010-03-12
After alot of searching, and trying a lot of different things, and still not getting headphones working. I'm just going to give up for now.

My problem is I didn't buy my computer from a company. I built it from parts I bought from Newegg.com. So it's tough to find a solution for my specific computer build.

Oh well...

---

### Post by RedSingularity on 2010-03-14
> **eminembdg said:**
> After alot of searching, and trying a lot of different things, and still not getting headphones working. I'm just going to give up for now.

My problem is I didn't buy my computer from a company. I built it from parts I bought from Newegg.com. So it's tough to find a solution for my specific computer build.

Oh well...

eminembdg, if you want to start a new thread maybe I could give you a hand.

---

### Post by Yellow Pasque on 2010-03-14
> **lift_test said:**
> Can anybody suggest what I can try?
```
gksu gedit /etc/modprobe.d/alsa-base.conf
```
Append this line:
```
options snd-hda-intel model=acer
```
Save. Reboot. See if it works.

---

### Post by lift_test on 2010-04-27
Just updated Karmic and sound is now working.

---

