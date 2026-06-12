---
title: "FIOS TV-in Help needed"
date: 2008-09-11
forum: Mythbuntu
---

### Post by 24jedi on 2008-09-11
EQUIPMENT:
FIOS digital service (Virginia, USA)
STB Motorola QIP 2500-3
Video-in Hauppauge WinTV-HVR 1600 with beta driver
Video-out nvidia e-GeForce 8600 GT
RAM 1.5g
CPU 2.8 dual core Intel
OS Mythbuntu v8.04
SchedulesDirect channel service (paid-4)
TV - Sony 32" 6-8 years old (COAX, RCA jacks and S-video only)
btw... I have found most all of my solutions at this forum. Now I've hit a wall and need some help.

**Partially running system:** Most everything works. I can download schedule, iTunes trailers, MythWeb, MythWeather ...etc.

I can't get the TV-in to work w/o STB.

1. MythTV will ONLY work when in-line between STB and TV. And this will only work with MythTV on channel 1. Any attempt to change channel on MythTV results in scrambled signal display (noise).

2. If I connect incoming COAX to TV, signal is scrambled. Nothing, Nada.

3. If I connect incoming COAX to MythTV, signal is scrambled as well. I've tried both NTSC and ATSC connector.

I was hoping to eliminate the Motorola STB or atleast wire MythTV in parallel, with a mechanical switchbox for determining which signal to send to TV.

Can anyone impart some wisdom on me ??

Is there a difference in signalling between OTA digital and digital Cable/Fiber medium ??

TIA.

---

### Post by bmwman on 2008-09-11
I think you need to have a IR blaster or other way to control the STB so when you change the channel in MythTv, it would change the channel on the STB. I would certainly keep an eye on your thread since I'm getting FiOS soon too. I live in NoVA as well and currently have COX cable and they SUCK!

---

### Post by jaakan on 2008-09-12
1. MythTV will ONLY work when in-line between STB and TV. And this will only work with MythTV on channel 1. Any attempt to change channel on MythTV results in scrambled signal display (noise)."

use a splitter, change you STB to a channel, and scan with myth TV
if the channel thats on your STB shows up on MYTHTV Your dealing with "Switched Digital Video" [http://electronics.howstuffworks.com/switched-digital-video.htm]("http://electronics.howstuffworks.com/switched-digital-video.htm")

Switched Digital Video - IE: only the channel you are watching is sent.

What setting are you using to scan in MYTHTV?
pick QAM256 - Cable standard ( you try HRC or IRC too) - hidden encrypted channels

2. If I connect incoming COAX to TV, signal is scrambled. Nothing, Nada.

-- if your TV doesn't support QAM you can't decode digital cable/fios-tv

I was hoping to eliminate the Motorola STB or atleast wire MythTV in parallel, with a mechanical switchbox for determining which signal to send to TV.

Can anyone impart some wisdom on me ??

Is there a difference in signalling between OTA digital and digital Cable/Fiber medium ??

yes, digital Cable/Fiber medium - both use QAM64 or QAM256 on top of MPEG2

---

