---
title: "nvidia hdmi mplayer help"
date: 2011-08-07
forum: Multimedia Software
---

### Post by kingmoffa on 2011-08-07
Hi, 

Im trying to get sound to work in mplayer for my myth tv box. 

My hardware setup is a nvidia motherboard with hdmi (not used) and a geforce 210 with hdmi (that is used). The hdmi is connect to an external amplifier that should handle most things. 

Sound works fine in mythtv - the audio output device used is:
ALSA:hdmi:Card=Nvidia_1,DEV=1

When I try using the command line speaker-test utility it all works:

speaker-test -Dplughw:2,7 -c6


However, aplay and mplayer both dont give any sound - with neither outputting any error messages. 

[INDENT]aplay -D plughw:2,7  /usr/share/sounds/alsa/Front_Center.wav 
Playing WAVE '/usr/share/sounds/alsa/Front_Center.wav' : Signed 16 bit Little Endian, Rate 48000 Hz, Mono

mplayer  -ao alsa:device=plughw=2.7 /usr/share/sounds/alsa/Front_Center.wav 

Playing /usr/share/sounds/alsa/Front_Center.wav.
Audio only file format detected.
==========================================================================
Opening audio decoder: [pcm] Uncompressed PCM audio decoder
AUDIO: 48000 Hz, 1 ch, s16le, 768.0 kbit/100.00% (ratio: 96000->96000)
Selected audio codec: [pcm] afm: pcm (Uncompressed PCM)
==========================================================================
AO: [alsa] 48000Hz 1ch s16le (2 bytes per sample)
Video: no video
Starting playback...
A:   1.0 (00.9) of 1.0 (01.0)  0.0% 

Exiting... (End of file)

[/INDENT]

Thankfully myth's internal player does play most things - its just videos taken with a phone that it stuggles with , and in mythgallery it will not use the internal player.


Any advice warmly welcomed.

---

### Post by BicyclerBoy on 2011-08-07
Don't use mplayer but..

mplayer  -ao alsa:device hw:2.7 -ac hwdts,hwac3,
(trailing comma is required)
this should play DTS AC3 via pass-thru' & everything else as 2ch PCM.

---

