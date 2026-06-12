---
title: "No surround with ES1371"
date: 2009-11-22
forum: Multimedia Software
---

### Post by Soldeace on 2009-11-22
I'm using Ubuntu Karmic and surround sound doesn't work. I have a Sound Blaster 5.1, although I suspect it's not genuine once it's recognized as Ensoniq 1371 and snd_ens1371 is loaded instead of snd_emu10k1. Anyway, it has surround support. The sound card has 5 connectors (3 of them are: black = rear out, green = front out and orange = center/LFE).

I double-checked everything, from volume sliders in alsamixer to PulseAudio's daemon-conf. Nothing works! Neither surround 4.0, 5.0 or 5.1. All I can get is a messy stereo sound.


Help is greatly appreciated!



This is what I hear when speaker-test is executed with Alsa under PulseAudio:

```

Speaker		($ speaker-test -c 5)
----------------------------------
CENTER		front-left
		front-center
		rear-left (low volume)

FRONT		front-left
		front-right
		front-center
		rear-left (low volume)
		rear-right(low volume)

REAR		front-left
		front-right
		front-center
```


And this is what happens when only Alsa is loaded:

```

Speaker		($ speaker-test -c 5)
----------------------------------
CENTER		front-left
		
FRONT		front-left
		front-right
		
REAR		front-left
		front-right
		
```

Please notice pure Alsa simply duplicates a stereo sound to front and rear channels and in a odd way, leaving the center speaker with one front channel.

This is the output of aplay:

```
$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: AudioPCI [Ensoniq AudioPCI], device 0: ES1371/1 [ES1371 DAC2/ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: AudioPCI [Ensoniq AudioPCI], device 1: ES1371/2 [ES1371 DAC1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

$ aplay -L
front:CARD=AudioPCI,DEV=0
    Ensoniq AudioPCI, ES1371 DAC2/ADC
    Front speakers
rear:CARD=AudioPCI,DEV=0
    Ensoniq AudioPCI, ES1371 DAC1
    Rear speakers
surround40:CARD=AudioPCI,DEV=0
    Ensoniq AudioPCI, ES1371 DAC2/ADC
    4.0 Surround output to Front and Rear speakers
iec958:CARD=AudioPCI,DEV=0
    Ensoniq AudioPCI, ES1371 DAC2/ADC
    IEC958 (S/PDIF) Digital Audio Output
null
    Discard all samples (playback) or generate zero samples (capture)
pulse
    Playback/recording through the PulseAudio sound server

```

And this is what happens when I run speaker-test with "-Dsurround40":

```
$ speaker-test -Dsurround40 -c 4 -twav

speaker-test 1.0.20

Playback device is surround40
Stream parameters are 48000Hz, S16_LE, 4 channels
WAV file(s)
ALSA lib setup.c:555:(add_elem) Cannot obtain info for CTL elem (MIXER,'AC97 2ch->4ch Copy Switch',0,0,0): No such file or directory
Playback open error: -2,No such file or directory

```


Screenshot of alsamixer:
[ATTACH]137197[/ATTACH]

lspci specs:

```
$ lspci -vv
05:06.0 Multimedia audio controller: Ensoniq ES1371 [AudioPCI-97] (rev 09)
	Subsystem: Ensoniq ES1371 [AudioPCI-97]
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=slow >TAbort- <TAbort+ <MAbort+ >SERR- <PERR- INTx-
	Latency: 32 (3000ns min, 32000ns max)
	Interrupt: pin A routed to IRQ 16
	Region 0: I/O ports at a000 [size=64]
	Capabilities: [dc] Power Management version 2
		Flags: PMEClk- DSI+ D1+ D2+ AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Kernel driver in use: ENS1371
	Kernel modules: snd-ens1371

```

PS: It's really strange "aplay -L" lists only surround40 and not surround51, although I've checked it's physically possible with this particular sound card. Either way none of these works.

Does it seem like a non-documented issue?

---

### Post by AgentZ86 on 2010-04-29
I have a problem with Ensoniq 1371 also which is soundblaster also

No sound in Karmic 9.10 64 bit

I seem to be missing a lot of controls on the alsamixer when compared to the image posted from the first poster here.

All indications says the sound card is detected and appears working, but alsamixer does not seem to indicate the ports are turned on, and I'm not sure how to turn them on if that is the problem.

Line In->Rear Out [Off] - What does this mean and do I need to turn it on ? 


Anyhow, any help is appreciated.
Thanks

---

### Post by lidex on 2010-04-29
Try gnome-alsamixer and make sure everything is enabled in 'Edit>Soundcard Properties'. Also check the 'Configuration' tab in pulseaudio volume control and your setup in 'System>Preferences>Sound'

---

### Post by AgentZ86 on 2010-04-29
> **lidex said:**
> Try gnome-alsamixer and make sure everything is enabled in 'Edit>Soundcard Properties'. Also check the 'Configuration' tab in pulseaudio volume control and your setup in 'System>Preferences>Sound'

Thanks for the reply, I'll play with things some more.

gnome-alsamixer produces the following error
Well first the terminal says:
> ** (gnome-alsamixer:22249): WARNING **: gam_toggle_get_state (). No idea what to do for mixer element "Mic Select"!

** (gnome-alsamixer:22249): WARNING **: gam_toggle_get_state (). No idea what to do for mixer element "Mono Output Select"!

Then the popup gui says:
> An error occurred while loading or saving configuration information for GNOME ALSA Mixer. Some of your configuration settings may not work properly.

I can either select OK or close and then get to the gnome-mixer gui

But I can also click details which produces this text in the window:
> Bad key or directory name: "/apps/gnome-alsamixer/toggle_display_names/Cirrus_Logic_CS4297A_rev_4-Line_In->Rear_Out": `>' is an invalid character in key/directory names
Bad key or directory name: "/apps/gnome-alsamixer/display_toggles/Cirrus_Logic_CS4297A_rev_4-Line_In->Rear_Out": `>' is an invalid character in key/directory names


Anyhow when I select in the gnome-alsa gui IEC958, and unmute the PCM volume I can then hear some sound, but very very distorted and weak

It sounds like I'm trying to hear a radio station that is not coming in and all you can hear is static with a very faint hint of sound way off in the background of the loud static.

So it would appear that the sound card is recognized and I see it in a tab of the gnome-alsamixer but no sound or only static digital sound, however I don't think I'm plugged to the digital output of the card only the green standard jack that also works fine when booting to windows xp.

Anyhow, if you have anything else I might try any advise is good advise.

Thanks

---

