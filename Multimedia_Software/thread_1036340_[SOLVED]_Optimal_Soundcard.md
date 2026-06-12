---
title: "[SOLVED] Optimal Soundcard"
date: 2009-01-10
forum: Multimedia Software
---

### Post by eckeroo on 2009-01-10
Hello all,

Using Hardy 8.04, I'm in the middle of finding out the best sound settings I can have for my PC with two speaker stereo. I have been reading bits from the thread [http://ubuntuforums.org/showthread.php?t=962695&highlight=Alsa+configuration](http://ubuntuforums.org/showthread.php?t=962695&highlight=Alsa+configuration)

To begin with, I have available to me three pieces of hardware:

1) Creative Soundblaster Live! Value, model CT4670 - [currently installed]

2) Creative Soundblaster Audigy with SB1349  model SB0090

3) Motherboard onboard Audio, Cmedia CMI8738

The motherboard is an ASUS A7M266 - a classic

From what I've read on [https://wiki.ubuntu.com/HardwareSupportComponentsSoundCardsCreativeLabs](https://wiki.ubuntu.com/HardwareSupportComponentsSoundCardsCreativeLabs) the Live! Value card is the one that works best with Ubuntu, but my CT4670 model number may not support Surround sound. From the same webpage, it appears the Audigy card cannot be fully utilised and can only work with the older emuk10k1 driver. And finally, there is the option of using the onboard audio instead of the other two, but I don't know yet if Ubuntu will support it.

I'm just beginning to learn about audio configurations. My goal in particular is to get the best possible DVD playback on VLC. I'm still reading up on ALSA and PulseAudio and from what I've read it may be worthwhile for me to upgrade to Intrepid 8.10 as it supposedly has a better audio setup. My current audio setup is on the Hardy default.

I can get Stereo 2.0 DVDs to play well on VLC. But the audio quality of my Surround 2.0 DVDs is marred by a slight and annoying 'skip' sound every minute or so.

Also, is it possible to utilise my S/PDIF [EIC958] connection from my DVD player to my Soundblaster Live! Value soundcard and will it improve the sound quality during DVD playback?

Please let me know what pieces of hardware and software I should use for best results.

much appreciated

---

### Post by markbuntu on 2009-01-10
The C-media 8738 is well supported and is a very good chipset for on-board sound. There is not a lot of difference between hardy and intrepid as far as sound support goes except Intrepid has a newer alsa version. I am not sure if the soundblaster drivers have changed between them.

Anyway, if you want to get your sound dialed in go here


[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by eckeroo on 2009-01-11
My DVD player is a HITACHI DVD-ROM GD-8000

on an online manual I found the following audio output capabilities:
> 
Audio 2 channels
(20 to 20,000 Hz) ± 3 dB Frequency Response 
0.1% (LPF 20 khZ, 1 khZ) max. Distortion 

Output levels
Headphones: 0.65 Vrms typical (Volume maximum, 32 ohms Load)
Line Out: 0.7 Vrms (47 kohms Load, Att=0dB) 

typical Output Terminals
Headphones: j  3.5mm Jack 
Line Out: 4-pin Terminal

Of the 'typical output terminals' There is no mention of any S/PDIF or EIC958 output. It does have a 2-pin digital socket, but it doesn't mention this facility anywhere in the manual. Do DVD-ROMS sometimes have false sockets on the back perhaps only utilised for better models? If so, this would explain why my S/PDIF isn't being detected - my DVD-ROM doesn't have that capability.

My interest has also turned to the audio codecs. I discovered that audio information along the S/PDIF cable is encoded with a AC-3 codec. ALSA or PulseAudio then has to decode the AC-3 info. Is there a good thread anywhere that can guide me through all the settings found on VLC Settings/Preferences?

---

### Post by eckeroo on 2009-01-11
I read this somewhere:

> Dolby Digital sound streams travel through the PCI bus to reach the decoder (or your soundcard) and the SPDIF socket on your DVD-ROM drive is not needed for this operation. The SPDIF socket your DVD-ROM drive is used for the transmission of digital audio from music CDs only, it has no other use. In fact, my old Panasonic 2X CD-ROM drive has this socket, and I've never had to use it.

Is this true I wonder?

---

### Post by eckeroo on 2009-01-11
As an experiment, I tried using the onboard audio. The slight audio skipping sound during DVD playback persisted exactly the same as before, which leads me to believe my problem is not a hardware/driver issue with the soundcard. My attention now is on the VLC settings.

The onboard audio was bad, there was a crackling sound and I had to turn the volume right up before I could hear anything. I'm therefore sticking with the Soundblaster Live! Value card.

I've also disconnected the 4-pin and 2-pin audio inputs to the soundcard as I've gathered that the DVD playback is all done through the IDE cable.

---

### Post by eckeroo on 2009-01-11
This thread should probably be in the Multimedia and Video category.

During DVD playback in VLC, under View/Stream_and_Media_info and then in the statistics tab, it is reported that there are Lost video frames and Lost Audio buffers, which would account for the 'slight' skipping noise I encounter during playback.

This still may be a hardware issue, as the lost video frames and audio buffers may be because of hardware limitations/lack of memory.

My system has 512MB PC2100 DDR memory
A7M-266 Athlon XP 1900+(Model 6)(Palomino)*

*actually operates at 1600MHz, Athlon XP 1900+ is the commercial name

---

### Post by eckeroo on 2009-01-15
My DVD playback problem was solved by following the instructions on this thread to configure PulseAudio correctly:

[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

My poor DVD playback performance must have been a result of the poorly configured PulseAudio on Hardy 8.04

---

### Post by zzzuppermen on 2009-03-04
> **eckeroo said:**
> I read this somewhere:



Is this true I wonder?

Just to add. Yes. S/PDIF is apparently audio only.

From wikipedia:

> S/PDIF specifies a Data Link Layer protocol and choice of Physical Layer specifications for carrying digital audio signals between devices and stereo components.

---

