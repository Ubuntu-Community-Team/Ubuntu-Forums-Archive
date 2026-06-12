---
title: "Trouble with Creative Audigy 2 ZS"
date: 2009-04-08
forum: Multimedia Software
---

### Post by guernicaaa on 2009-04-08
Hey all,
I installed Ubuntu 8.10 about a month ago to use for programming for the classes that I'm taking.  For the first week, I was able to listen to my music off my main drive and it was great.  But out of nowhere, the sound stopped working.  I have a Create SB Audigy 2 ZS.  I tried that Comprehensive Sound Guide thread and had no luck.  I'm positive all my volumes are up and stuff like that.  I dunno what happened.  Help please?
I ran:

matt@matt-desktop:~$ lspci -v | grep Audigy
05:00.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)
	Kernel driver in use: EMU10K1_Audigy
05:00.1 Input device controller: Creative Labs SB Audigy Game Port (rev 04)
05:00.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port (rev 04) (prog-if 10)
matt@matt-desktop:~$ sudo modprobe snd-emu10k1

and still no luck.  thanks

---

### Post by mc4man on 2009-04-08
Could be the Analog/Digital Output Jack. The function was reversed in an update.
To check. double click on the speaker icon in top panel and look for a 'switches' tab. If it's there then open and uncheck the 'Analog/Digital Output Jack'

If not there then click on 'preferences', scroll down and enable the Analog/Digital Output Jack switch, then go back and uncheck.

Note i don't have pulseaudio so the switch, preferences (alsamixer) is always available, if you see neither then post back.

---

### Post by guernicaaa on 2009-04-20
> **mc4man said:**
> Could be the Analog/Digital Output Jack. The function was reversed in an update.
To check. double click on the speaker icon in top panel and look for a 'switches' tab. If it's there then open and uncheck the 'Analog/Digital Output Jack'

If not there then click on 'preferences', scroll down and enable the Analog/Digital Output Jack switch, then go back and uncheck.

Note i don't have pulseaudio so the switch, preferences (alsamixer) is always available, if you see neither then post back.

Wow, I can't believe it was something that simple.  Thanks so much for your help!!!

---

### Post by Geoffzx6r on 2009-04-24
I have an audigy 2 as well but that fix isn't working for me. I have no clue what's going on.



```
06:05.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)
	Subsystem: Creative Labs Device 1003
	Flags: bus master, medium devsel, latency 32, IRQ 17
	I/O ports at 1000 [size=64]
	Capabilities: <access denied>
	Kernel driver in use: EMU10K1_Audigy
	Kernel modules: snd-emu10k1

```

here's the output for aplay -l

```
**** List of PLAYBACK Hardware Devices ****
card 0: Audigy2 [Audigy 2 ZS [SB0353]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
  Subdevices: 31/32
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
  Subdevice #8: subdevice #8
  Subdevice #9: subdevice #9
  Subdevice #10: subdevice #10
  Subdevice #11: subdevice #11
  Subdevice #12: subdevice #12
  Subdevice #13: subdevice #13
  Subdevice #14: subdevice #14
  Subdevice #15: subdevice #15
  Subdevice #16: subdevice #16
  Subdevice #17: subdevice #17
  Subdevice #18: subdevice #18
  Subdevice #19: subdevice #19
  Subdevice #20: subdevice #20
  Subdevice #21: subdevice #21
  Subdevice #22: subdevice #22
  Subdevice #23: subdevice #23
  Subdevice #24: subdevice #24
  Subdevice #25: subdevice #25
  Subdevice #26: subdevice #26
  Subdevice #27: subdevice #27
  Subdevice #28: subdevice #28
  Subdevice #29: subdevice #29
  Subdevice #30: subdevice #30
  Subdevice #31: subdevice #31
card 0: Audigy2 [Audigy 2 ZS [SB0353]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 0: Audigy2 [Audigy 2 ZS [SB0353]], device 3: emu10k1 [Multichannel Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Audigy2 [Audigy 2 ZS [SB0353]], device 4: p16v [p16v]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

I'm getting confused by this whole thing. I did the install of gnome-alsamixer and checked the one box. I booted into the bios already and checked to make sure the onboard was turned off and sure enough it is.

---

### Post by fletchoid on 2009-04-25
Thanks. Solved my problem too.  Stupid little thing caused a chain of events that had me wanting to uninstall 9.04  All is well now.  Thanks to Ubuntu community.

---

### Post by w1ntermute on 2009-07-22
I believe I have a very similar issue described here

I am on laptop with a microphone jack and inbuilt speakers (which I assume are denoted as 'front'). My audio works fine - but only through the microphone jack with a headset plugged in. Otherwise, no sound comes from the speakers at all.

I tried going to the 'switches' panel as described, but can find no such selection for audio jacks, even in the preferences. I only have Headphones, Front and PCM. Obviously I have tried to uncheck headphones to no avail.

Can anybody offer some assistance?

---

### Post by bcschmerker on 2010-02-09
I have a more specific issue related to the Audigy 2 ZS.  I recently retrofitted an Audigy 2 Drive to my AMD/Gigabyte-equipped Everex, already equipped with a Creative Laboratories SB0350 (CA0102 chipset, ALSA emu10k1 driver).  Analog inputs on the Audigy 2 Drive pick up just fine on both mix busses of my SB0350, incl. a short recording test on the Capture bus; no chance to test the digital-audio ins just yet due to lack of ***patible hardware.  What I'm having trouble on is getting the hardware synthesizer on the SB0350, and the MIDI I/O on the Audigy 2 Drive, to function and ***municate with a Cakewalk/Roland MIDI adapter on my eMachines/Acer EL1210-09 (a Windows box that I use for video streaming, as LiveVideo and Stickam are uncooperative with LinUX boxes).

To date, I have been unable to get a valid recording of streamed ***mands on the MIDI In despite correct adapters from the aforementioned EL1210-09.  The following Devices for Sound are detected on my system (as reported by ls /dev/snd):
```
controlC0 controlC1 controlC2
hwC0D0 hwC2D0 hwC2D2
midiC2D0 midiC2D1 midiC2D2 midiC2D3
pcmC0D3p pcmC1D0c pcmC2D0c pcmC2D0p pcmC2D1c pcmC2D2c pcmC2D2p pcmC2D3p pcmC2D4c pcmC2D4p
seq
timer
```
What initialization issues, if any, exist for the Audigy 2 Drive?  The answer may help me get my music on track.

Update:  This is the StdOut from aplay -l, which reports 41 Subdevices among five Devices (four belonging to my SB0350, one to an ATI/AMD HDMI interface):
```
**** List of PLAYBACK Hardware Devices ****
card 0: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: Audigy2 [Audigy 2 ZS [SB0350]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
  Subdevices: 32/32
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
  Subdevice #8: subdevice #8
  Subdevice #9: subdevice #9
  Subdevice #10: subdevice #10
  Subdevice #11: subdevice #11
  Subdevice #12: subdevice #12
  Subdevice #13: subdevice #13
  Subdevice #14: subdevice #14
  Subdevice #15: subdevice #15
  Subdevice #16: subdevice #16
  Subdevice #17: subdevice #17
  Subdevice #18: subdevice #18
  Subdevice #19: subdevice #19
  Subdevice #20: subdevice #20
  Subdevice #21: subdevice #21
  Subdevice #22: subdevice #22
  Subdevice #23: subdevice #23
  Subdevice #24: subdevice #24
  Subdevice #25: subdevice #25
  Subdevice #26: subdevice #26
  Subdevice #27: subdevice #27
  Subdevice #28: subdevice #28
  Subdevice #29: subdevice #29
  Subdevice #30: subdevice #30
  Subdevice #31: subdevice #31
card 2: Audigy2 [Audigy 2 ZS [SB0350]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 2: Audigy2 [Audigy 2 ZS [SB0350]], device 3: emu10k1 [Multichannel Playback]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 2: Audigy2 [Audigy 2 ZS [SB0350]], device 4: p16v [p16v]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```See also "[JACK/ALSA Connection Issues on 8.04.4 with Creative SB0350](http://ubuntuforums.org/showthread.php?t=1405252)."

---

### Post by bcschmerker on 2010-03-10
> **bcschmerker said:**
> ...What I'm having trouble on is getting the hardware synthesizer on the SB0350, and the MIDI I/O on the Audigy 2 Drive, to function and communicate with a Cakewalk/Roland MIDI adapter on my eMachines/Acer EL1210-09 (a Windows box that I use for video streaming, as LiveVideo and Stickam are uncooperative with LinUX boxes).

To date, I have been unable to get a valid recording of streamed commands on the MIDI In despite correct adapters from the aforementioned EL1210-09....Update:  I retrieved a hardware Bug from ALSA-Project.org concerning the Audigy 2 Drive.  Digital-audio ins on the Drive, I found, were fully operational; not so the MIDI I/O, per the excerpt from /Main/Index.php/Matrix:Module-emu10k1 at ALSA-Project.org retrieved 09 March 2010:
> There is an issue with the Audigy 2 Platinum Ex soundcard and the Audigy 4 pro (and probably some other Audigy 2 cards as well), whereas the IR sensor, MIDI and the buttons on the LiveDrive do NOT work at all until the LiveDrive is initialized by sending the sequence of '0xf0, 0x00, 0x20, 0x21, 0x61, 0x0, 0x00, 0x00, 0x7f, 0x0, 0xf7' to the MIDI port. Before doing this, even the LED on the LiveDrive won't blink, as it usually does when a button on the remote is pressed. As far as I know, this behaviour is different than with most LiveDrives manufactured by Creative.

---

### Post by WhoDaBear on 2010-06-03
> **mc4man said:**
> Could be the Analog/Digital Output Jack. The function was reversed in an update.
To check. double click on the speaker icon in top panel and look for a 'switches' tab. If it's there then open and uncheck the 'Analog/Digital Output Jack'

If not there then click on 'preferences', scroll down and enable the Analog/Digital Output Jack switch, then go back and uncheck.

Note i don't have pulseaudio so the switch, preferences (alsamixer) is always available, if you see neither then post back.

OK, you are indeed a hero.  This has been doing my head in for, well, ages.  Thanks Ubuntu community and forum folks.

---

