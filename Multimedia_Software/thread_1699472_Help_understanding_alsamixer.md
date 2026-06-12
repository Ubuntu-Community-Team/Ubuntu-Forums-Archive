---
title: "Help understanding alsamixer"
date: 2011-03-03
forum: Multimedia Software
---

### Post by tbridges42 on 2011-03-03
I've just got ALSA working on a minimal Ubuntu 10.04 install, but I'm having trouble getting sound to the back speakers. I have an old quadrophonic stereo hooked up to XBMC, which is set for 4.0 output. When I first got the sound working, I had very very quiet sound out of the back, and in trying to boost the volume, I lost it entirely.

I think the problem is I have no idea what half these channels are. My alsamixer lists:

Master (obvious)
Master Mono
Headphone
3D Control - Center <--
3D Control - Depth  <-- I have no idea what these are
3D Control - Switch <--
PCM                       <--
Front (controls my front volume)
Surround (No effect)
Center (I don't have a center speaker)
Center/LFE Exchange
LFE
Line
CD
Mic
Mic Boost
Mic Select
Phone
S/PDIF
S/PDIF Output
S/PDIF Playback
PC Speaker
Aux
Mono Out
Alternative Level to Surround Out
Downmix LFE and Center to Front
Downmix Surround to Front
External Amplifier
Input Source Select (2 of these)
Smart 5.1 Select

I can get by with just front audio, but I'd really like to get the rear speakers working before I take the keyboard off.

---

### Post by rayj on 2011-03-03
Got a similar setup (4.0 surround configuration, quad receiver/amp). My motherboard supports discrete outputs, and the rear speakers seem bundled to the 'surround' virtual fader. The motherboard soundcard's analog audio out is a bit noisy, as most are.

It might be a good idea to get a surround test suite of some sort rolling...I used a Radio Shack optical drive brush/AV configuration disk.

I typically use VLC for video playback, and with surround decoding enabled (not AUTO), it works out of the box. Without AC3 compression, the surround effects might be too quiet to be heard in your environment, depending on source. 

Keep in mind, a lot of older surround schemes (pro logic and whatnot) simply take corresponding front channels, invert the phase, and aim it back at the main speakers with delay. Unless you are sure you are feeding it a proper surround stream, and decoding it properly, results will vary per source.

---

### Post by prankstar008 on 2011-03-04
How is the stereo hooked up? (ie. 3.5mm, spdif...) Someone correct me if I'm wrong, but PCM is a pretty important channel to have turned up. Also, have you swapped the speakers out for something else, say powered desktop speakers... That way you can rule out a config issue w/ the stereo (although you may know for sure that its the computer, just thought I'd suggest it)

---

