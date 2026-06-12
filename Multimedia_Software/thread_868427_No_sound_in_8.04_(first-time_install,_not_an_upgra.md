---
title: "No sound in 8.04 (first-time install, not an upgrade)"
date: 2008-07-23
forum: Multimedia Software
---

### Post by alhead on 2008-07-23
A few weeks ago I installed Hardy Heron onto my Toshiba Satellite M45 (completely switched from XP, not dual-boot).  I'm really enjoying using Ubuntu, but I haven't been able to get the sound working.  This is my first time using Linux, so I don't really know what I'm doing.  I've gone through the Comprehensive Sound Problem Solution Guide and other posts, but with no success.

The output of "aplay -l" is

**** List of PLAYBACK Hardware Devices ****
card 0: ICH6 [Intel ICH6], device 0: Intel ICH [Intel ICH6]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: ICH6 [Intel ICH6], device 4: Intel ICH - IEC958 [Intel ICH6 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

I think this means that Ubuntu sees my sound card, but I'm not that familiar with the area.

The partial output of "lspci -v" is

00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 04)
	Subsystem: Toshiba America Info Systems Unknown device ff10
	Flags: bus master, medium devsel, latency 0, IRQ 10
	I/O ports at e100 [size=256]
	I/O ports at e200 [size=64]
	Memory at d0180000 (32-bit, non-prefetchable) [size=512]
	Memory at d0180200 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

I've confirmed that alsamixer has everything turned up and not muted.  I've also checked the External Amplifier problem.

I found a post about adding "snd-intel8x0 ac97_quirk=3" to "/etc/modprobe.d/alsa-base" but this has not helped me.  I also set my default sound card to ICH6 using "sudo apt-get install asoundconf-gtk && asoundconf-gtk" but still no sound.

Sometimes upon returning from standby I hear a stuttering sound that I'm assuming is an attempt to play a welcome noise.  This is the only time the computer emits any sound.  Occasionally when I click mute or unmute (in blind attempts to magically fix it) the speakers make a popping noise, but do not play any sort of tone.

I also attempted to turn off any sound drivers in my BIOS, but none were listed.

I've tried to give as much information as possible here, in hopes that someone will be able to help me.  I've been really happy with Ubuntu other than being unable to hear anything.  I'd really like to get the sound working, but I don't know where to go from here.

Thanks.

---

### Post by alhead on 2008-07-25
I have some more information.  Today I was bringing my computer back from standby, and before the GUI loaded, I noticed some text that said "Disabled IRQ 10" or something like that.  I know that the sound card is IRQ 10 from lspci -v.  I don't know if this could help solve the problem, but it seems relevant.

---

### Post by Mark76 on 2008-07-25
Same problem, but this time from a reinstall

> aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
            $ lspci -v
00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
	Subsystem: Hewlett-Packard Company Unknown device 2a61
	Flags: bus master, 66MHz, fast devsel, latency 0
	Capabilities: <access denied>

00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
	Subsystem: Hewlett-Packard Company Unknown device 2a61
	Flags: bus master, 66MHz, fast devsel, latency 0

00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
	Subsystem: Hewlett-Packard Company Unknown device 2a61
	Flags: 66MHz, fast devsel, IRQ 255
	I/O ports at fc00 [size=64]
	I/O ports at 1c00 [size=64]
	I/O ports at f400 [size=64]
	Capabilities: <access denied>

00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
	Subsystem: Hewlett-Packard Company Unknown device 2a61
	Flags: 66MHz, fast devsel

00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3) (prog-if 10 [OHCI])
	Subsystem: Hewlett-Packard Company Unknown device 2a61
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 16
	Memory at fe02f000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3) (prog-if 20 [EHCI])
	Subsystem: Hewlett-Packard Company Unknown device 2a61
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 17
	Memory at fe02e000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1) (prog-if 01 [Subtractive decode])
	Flags: bus master, 66MHz, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
	I/O behind bridge: 0000b000-0000bfff
	Memory behind bridge: fd800000-fd8fffff
	Prefetchable memory behind bridge: fdf00000-fdffffff
	Capabilities: <access denied>

00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
	Subsystem: Hewlett-Packard Company Unknown device 2a61
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 16
	Memory at fe024000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2) (prog-if 8a [Master SecP PriP])
	Subsystem: Unknown device f03c:2a61
	Flags: bus master, 66MHz, fast devsel, latency 0
	[virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
	[virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
	I/O ports at f000 [size=16]
	Capabilities: <access denied>

00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
	Subsystem: Hewlett-Packard Company Unknown device 2a61
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 220
	Memory at fe02d000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at ec00 [size=8]
	Capabilities: <access denied>

00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2) (prog-if 85 [Master SecO PriO])
	Subsystem: Hewlett-Packard Company Unknown device 2a61
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 19
	I/O ports at 09f0 [size=8]
	I/O ports at 0bf0 [size=4]
	I/O ports at 0970 [size=8]
	I/O ports at 0b70 [size=4]
	I/O ports at d800 [size=16]
	Memory at fe02c000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

00:08.1 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2) (prog-if 85 [Master SecO PriO])
	Subsystem: Hewlett-Packard Company Unknown device 2a61
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 19
	I/O ports at 09e0 [size=8]
	I/O ports at 0be0 [size=4]
	I/O ports at 0960 [size=8]
	I/O ports at 0b60 [size=4]
	I/O ports at c400 [size=16]
	Memory at fe02b000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 0000a000-0000afff
	Memory behind bridge: fde00000-fdefffff
	Prefetchable memory behind bridge: 00000000fdd00000-00000000fddfffff
	Capabilities: <access denied>

00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	I/O behind bridge: 00009000-00009fff
	Memory behind bridge: fdc00000-fdcfffff
	Prefetchable memory behind bridge: 00000000fdb00000-00000000fdbfffff
	Capabilities: <access denied>

00:0c.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	I/O behind bridge: 00008000-00008fff
	Memory behind bridge: fda00000-fdafffff
	Prefetchable memory behind bridge: 00000000fd900000-00000000fd9fffff
	Capabilities: <access denied>

00:0d.0 VGA compatible controller: nVidia Corporation GeForce 6100 nForce 430 (rev a2) (prog-if 00 [VGA controller])
	Subsystem: Hewlett-Packard Company Unknown device 2a61
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 5
	Memory at fb000000 (32-bit, non-prefetchable) [size=16M]
	Memory at e0000000 (64-bit, prefetchable) [size=256M]
	Memory at fc000000 (64-bit, non-prefetchable) [size=16M]
	[virtual] Expansion ROM at 50000000 [disabled] [size=128K]
	Capabilities: <access denied>

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

01:09.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80) (prog-if 10 [OHCI])
	Subsystem: Hewlett-Packard Company Unknown device 2a61
	Flags: bus master, stepping, medium devsel, latency 64, IRQ 18
	Memory at fd8ff000 (32-bit, non-prefetchable) [size=2K]
	I/O ports at bc00 [size=128]
	Capabilities: <access denied>


---

### Post by stoop1d m0nkey on 2008-07-25
Yes, I have the same problem... A new install...
```

**** List of PLAYBACK Hardware Devices ****
card 0: ICH5 [Intel ICH5], device 0: Intel ICH [Intel ICH5]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH5 [Intel ICH5], device 4: Intel ICH - IEC958 [Intel ICH5 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Live [Dell Sound Blaster Live!], device 0: emu10k1x [EMU10K1X Front]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Live [Dell Sound Blaster Live!], device 1: emu10k1x [EMU10K1X Rear]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Live [Dell Sound Blaster Live!], device 2: emu10k1x [EMU10K1X Center/LFE]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

and then for my lspci I get:

```

00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
	Subsystem: Dell Unknown device 0174
	Flags: bus master, medium devsel, latency 0, IRQ 21
	I/O ports at ee00 [size=256]
	I/O ports at edc0 [size=64]
	Memory at febffa00 (32-bit, non-prefetchable) [size=512]
	Memory at febff900 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

```

I checked my alsamixer and turn everything on....
Any help appreciated.....

---

### Post by alhead on 2008-09-06
Mark76 and stoop1d m0nkey, did you guys ever find a solution for your problem?  At this point, I'm basically waiting to see if Ibex will magically fix it.

---

### Post by Mark76 on 2008-09-06
Yeah. I think one of the channels was muted in alsa.

---

### Post by dmurat on 2008-09-06
exactly the same problem with you, alhead. i did the same things as you and the results were the same as you. 
the only thing i hear is buzz buzzz like things. its like, the system is trying to speak but cant :D
i hope someone can come up with a solution

edit: i now saw the "Capture", "Mix" and "External Amplifier" are muted in alsa and their buttons are disabled. i cant mute them. what can i do?

---

### Post by dmurat on 2008-09-06
have you guys found any solution or something? or you are just running the system without sound for months..?

---

### Post by ThymeTraveler on 2008-09-06
I have the same problem - except that there is absolutely NO sound, not even clicking or chatter.  I did notice that IRQ 20 is assigned to the audio device and one of the USB Controllers.  Is this the problem?

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
        Subsystem: Dell Unknown device 01f1
        Flags: bus master, fast devsel, latency 0, IRQ 20
        Memory at fe9fc000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>


00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Dell Unknown device 01f1
        Flags: bus master, medium devsel, latency 0, IRQ 20
        I/O ports at 6f60 [size=32]




Thyme

---

### Post by ThymeTraveler on 2008-09-06
Never mind.  This fixed my sound problem:

sudo /etc/init.d/alsa-utils reset

Thyme
:)

---

### Post by alhead on 2008-09-08
> **dmurat said:**
> have you guys found any solution or something? or you are just running the system without sound for months..?

I've been running it without sound for months...

I haven't tried Thyme's fix yet, though.  I'm on a different computer.

---

### Post by alhead on 2008-09-08
Thyme's fix didn't work for me... :(

---

### Post by Mark76 on 2008-09-10
I had to reinstall yesterday and the sound problem came back this morning.  I went through the previous steps again, to no avail.

Here's what I got when I tried to add the rox desktop device handler to my panel

>  couldn't add the device '/org/freedesktop/Hal/devices/pci_10de_3f0_sound_card_0_alsa_control__1' because there's an error in the handler for Soundcard Mixers (ALSA)!

---

### Post by Mark76 on 2008-09-10
Gah!

The stupid thing started working again just after I posted that last message.

Damn it, Ubuntu. If you're going to be be broken, at least be consistent about it :p

---

### Post by Yellow Pasque on 2008-09-10
You could always try OSS4..
[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)

---

### Post by powerbookluv111 on 2008-10-21
> **alhead said:**
> Thyme's fix didn't work for me... :(

Me either, same sound card as everyone else on a Gateway M250.

---

### Post by powerbookluv111 on 2008-10-27
Okay, So I finally got audio working! After going through multiple possible solutions and such, I finally just got it to work. Although I cannot tell you what the exact fix was, I can tell you witch modules I have set to load and how I got them to work. My /etc/modprobe.d/alsa-base file looks in the section where you add lines beginning with "options" to set modules to load for alsa. So [COLOR="Blue"]this[/COLOR] is the section:


# Load snd-seq for devices that don't have hardware midi;
#   Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
#   non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe -Qb snd-seq ; }
# Prevent abnormal drivers from grabbing index 0
options snd-intel8x0 index=0

# Ubuntu #62691, enable MPU for snd-cmipci
[COLOR="Blue"]options snd-hda-intel model=laptop
options snd-hda-intel model=gateway
options snd-hda-intel model=m2-2
options snd-hda-intel model=ref
option snd_intel8x0 ac97_quirk[/COLOR]

It was the option snd_intel8x0 ac97_quirk module that I used that finally worked. Then, double click on the speaker icon in the tray to open The volume control. 
Go to edit>preferences>
and make sure the following "tracks to be visible" are selected:
-Master
-Headphone
-PCM
-Line-in
-CD
-Microphone
-IEC958                       **********important**********
-IEC958 Playback AC97-SPSA    **********important**********
-PC Speaker
-External Amplifier            ****the most important right here*******

A new tab "switches" should appear in the mixer. Go to it, under external amplifier, UNCHECK the box. IEC 958 should be checked. 

Note that some devices such as IEC958 and IEC958 Playback AC97-SPSA may appear a little differently. Just make sure that external amplifier is unchecked and you have a "switches" section.

Also, some sort of ALSA extras may have to be installed for this (I can't remember what I installed) so, if a module won't load or something, Google around or check the forums to check what you need to install to get it. 

Hope this all helps! If you have a question or something, you can PM me or whatever, I'm not fantastic with Linux yet, still learning, but I can try and offer some help. :)

Good luck!

---

### Post by alhead on 2008-11-02
Well, I don't know exactly what happened, but installing 8.10 made sound magically work.  I don't know if I should mark this as solved, though, since the original problem was no sound in 8.04...

---

### Post by mibry on 2008-11-14
Hi, after reading this thread the command provided help to get sound to work.

MB

---

