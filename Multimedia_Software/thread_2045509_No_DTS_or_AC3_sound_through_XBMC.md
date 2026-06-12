---
title: "No DTS or AC3 sound through XBMC"
date: 2012-08-21
forum: Multimedia Software
---

### Post by roman84 on 2012-08-21
So I've been banging my head against the wall with this for a while and finally decided to ask for some help. I apologize in advance if this is a repost as I have seen similar topics on this forum but none that have proved useful in fixing my issue. Anyway, this is my problem:

I'm running Ubuntu 12.04 on a HTPC (using a Radeon 6570 card) with XBMC installed on it. My computer is connected to my TV through HDMI, and the TV is connected to my DTS-capable audio receiver via an optical cable. When I play video files containing DTS audio through VLC everything works fine, but when I go through XBMC I get no sound (I get the "failed to initialize audio" error). If I tell XBMC to pass everything as stereo, then I get sound through all speakers, but there is a lot of feedback. If I uncheck the DTS and AC3 radio buttons in the audio settings menu, I get sound, but only out of the front left and right speakers (2.0 instead of 51). When I play music through XBMC, I get sound out of all speakers, but that's not exactly a DTS signal. I've tried removing pulseaudio, but that disables audio entirely and removes all sound devices under the sound settings menu (System Settings -> Sound). Running aplay -l does display the graphics card. 

I'm relatively new to this, so any help is greatly appreciated!

---

### Post by BicyclerBoy on 2012-08-22
The best connection is HDMI thru' the AVR to display.

The display TV can not transcode audio formats..Some will only output stereo over optical (except from internal receiver/tuner).
Some TVs will pass-thru AC3 & DTS.

VLC must be using DTS S/PDIF pass-thru over HDMI & XBMC could be using HDA multi-channel LPCM (HDMI only).

You might have find a way to select the HDMI iec958/spdif audio device in XBMC..

When you refer to "audio settings menu".. do you mean XBMC or pavucontrol ?

The stock ubuntu audio config tool is rubbish.

---

### Post by roman84 on 2012-08-22
Unfortunately, my receiver does not have a hdmi input or output, only optical and digital coaxial. 

When I say "audio settings menu," I mean the one in xbmc. There is a hdmi ice958 option in xbmc for the pass through device, but when I select that, I get no sound. The audio output device in xbmc is set to my graphics card. I'll try to connect the receiver to the htpc directly and see if that works, but I was hoping to avoid that.

---

### Post by BicyclerBoy on 2012-08-22
The pass-thru' datastream is very fragile..
You can't use volume control or dmix.

Note that VLC & XBMC have a built-in AC3 encoder that can output over iec958 (S/PDIF or HDMI).

When you played the DTS media in VLC did the DTS "light-up" on the AVR/HT-amp ?

One problem you have is that HDMI reports the audio capabilities via ELD/EDID.
There is no reporting via IEC958.
So your video card reports the TV audio capabilities to alsa; this does not match the iec958 output (from TV).

You could install/run "pavucontrol" & use this to play around with audio setup..
Note that VLC & XBMC & mythtv can completely override this system setting.

---

### Post by walker195 on 2012-08-22
i believe xbmc has an auto detect feature try that sorry thats all i can think of

---

### Post by roman84 on 2012-08-24
So after spending way too much time playing around with the setup and settings I seem to have come across a couple of solutions that work. First, the only way I can get "DTS" to light up on the receiver is if I plug in the htpc directly via the optical cable, in which case audio works fine in xbmc. I was also able to use a combination of what you suggested and get xbmc to output 5.1 audio through my original setup (hdmi to tv, optical to receiver) by adjusting the pavucontrol settings and unchecking the AC3/DTS capable receiver buttons in xbmc. The audio quality appears to be better than if I just set xbmc to output everything as stereo, so I guess my question is in what format is the audio being sent to the receiver? Anyway, thank you very much for your help as I now have a functional htpc!

---

### Post by BicyclerBoy on 2012-08-24
Your DTS light result suggests that the TV does not pass-thru' DTS.

Does your amp indicate AC3?

Having to unselect AC3/DTS in pavucontrol suggests your TV does not pass-thru' DTS/AC3.

It is possible that pulse-audio downmix (5.1 --> 2ch) is better configured than XBMC.

iec958/SPDIF only supports 2 ch stereo PCM or encoded DTS/AC3.
There are different bitrates/sample rates.

Stereo PCM can be as high as 96KHz/24bit(32bit) (some go to 192KHz).
AC3 maxes out at 640Kbps (48KHz) DTS maxes at 1.5Mbps (48KHz). 

You can't get real 5.1 audio over iec958 without AC3/DTS.
Maybe your AVR uses Fake 5.1 prologic playback from stereo.

But I would think the downmixing coefficients (balance & time delays) would be a factor in AQ.

It is possible that you need to use the AMD catalyst driver to get HDMI audio to work properly..
The Radeon driver supports HDMI on some h/w..I don't use AMD.

---

### Post by roman84 on 2012-08-28
Unfortunately, my receiver only indicates DTS audio, not AC3, so I don't know what it's actually outputting to the speakers unless it is true DTS. And I had to unselect AC3/DTS capable receiver radio buttons in xbmc, not pavucontrol. In pavucontrol, I just turned on all audio options (PCM, AC3, DTS, etc.). The only driver I installed for my GPU was the fglrx one (the one that it allowed me to install through the Settings menu). I'll try installing the catalyst driver and see where that takes me. You might be right  about the tv not being able to pass-through DTS audio, so I'll try to play a blu ray through my ps3 and see what the receiver indicates (since the connection is the same as the htpc).

---

### Post by BicyclerBoy on 2012-08-29
[http://www.x.org/wiki/RadeonFeature#Radeon_Display_Hardware](http://www.x.org/wiki/RadeonFeature#Radeon_Display_Hardware)

This indicates radeon driver supports HDMI audio on NorthernIsland but kernel 3.5 is required..

Kernel 3.5 is avail in xorg-edgers ppa along with up-to-date radeon driver & fglx.

---

### Post by roman84 on 2012-09-06
I tried installing kernel 3.5, but I must have screwed something up because that messed up my system entirely (probably didn't remove something correctly before installing the new kernel). I did a clean reinstall of 12.04 last night and will start over with that. On a slight side note, is there a simple way to test what type of audio signal my TV actually passes through (aside from looking on the receiver and seeing if the DTS light comes on)?

---

### Post by BicyclerBoy on 2012-09-07
Did you use the xorg-edgers kernel ?
They strongly recommend using all their packages together or none..

That kernel broke broadcomm wifi on some netbooks; small code mod needed to the wifi driver code.

Did the X server (GUI desktop) not start/load correctly?

A "good" HT amp/AVR displays data stream format, num channels & clock rate.
The TV spec sheet could detail the pass-thru' capability.

But silence or blinking PCM symbol/icon & no data text indicates no data on my amp.

---

