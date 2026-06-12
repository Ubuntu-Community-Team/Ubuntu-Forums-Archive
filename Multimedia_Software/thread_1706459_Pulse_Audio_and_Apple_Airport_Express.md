---
title: "Pulse Audio and Apple Airport Express"
date: 2011-03-13
forum: Multimedia Software
---

### Post by Notre on 2011-03-13
Hi,

I apologize in advance if the best protocol is to tack my question on to an existing forum post regarding this subject, or create my own thread as I'm doing now.  Please feel free to direct me to a specific existing thread, if that is more appropriate.

At any rate, I have Ubuntu 10.04 and I'm trying to stream audio to an Apple Airport Express (the newer wireless N variety) via Pulse Audio.  I do get audio playing pretty easily, and I can listen to pretty much any audio stream, which is really great.  The problem I'm having is that the audio is skipping/stuttering when streamed over the Airport Express.

What I've tried to date for trouble shooting is:
- Audio from my Macbook (OS X) and iTunes streams flawlessly (after much tweaking with channels,etc)
- Audio playing directly on my Ubuntu computer, not streaming to Airport Express, plays fine
- I tried relocating the Airport Express and speakers to the same room as my Ubuntu computer and other wireless router (Airport Extreme) but the skipping/stuttering persists
- I installed Wicd network manager, as it apparently helped someone else, but no luck for me
- I get horrible stuttering with Rhythmbox, playing local AAC files and much less stuttering (but still present) when streaming audio from Grooveshark in Chrome
- I tried changing the default.pa file
a) tried adding #load-module module-hal-detect tsched=0 and commenting all the below out:

### Automatically load driver modules depending on the hardware available
#.ifexists module-udev-detect.so
#load-module module-udev-detect
#.else
### Alternatively use the static hardware detection module (for systems that
### lack udev support)
#load-module module-detect
#.endif

doing this, I could get no audio at all, including no internal audio (and volume control appears disabled).
b) remove above change default.pa and tried this instead:

### Automatically load driver modules depending on the hardware available
.ifexists module-udev-detect.so
load-module module-udev-detect tsched=0
.else
### Alternatively use the static hardware detection module (for systems that
### lack udev support)
load-module module-detect tsched=0
.endif

I don't even know if add "tsched=0" in the two places above even makes sense, but I noticed no differences at all.

At this point, I don't know what to try, but would be happy to try any suggestions anyone has.

Thanks for taking the time to read this!

---

### Post by MikaelHolber on 2011-04-12
Hi,

I think I done the same research as you did (pretty much) and I think that I know what the problem is but not the solution. I have two machines at home:
[LIST]
[*]Imac 24" with ubuntu and OSX, works from OSX without shuttering but not ubuntu (sometimes for minutes but usually not very long before the shutter starts)
[*]Asus EEEpc netbook with n-network. ubuntu with pretty much the same configuration
[/LIST]

Problem seems to be network latency. Worst shutter is from the Imac with the proprietary driver and N on the router (if the AEX is tethered via cable). This gives me a speed of 2mbit on the wifi and no sound almost from the AEX.
In the same configuration the eeepc playback is fine. Only during very heavy trafic such as two or more computers sucking torrents will the sound shutter.

The latency problem seems to be in the RAOP module and our only hope seems to be if they manage to update this one. 

I dont know if the cracking of the secret airport express key will change anything for the developers [http://www.engadget.com/2011/04/11/shairport-emulator-cracks-open-the-door-for-more-unofficial-airp/]("http://www.engadget.com/2011/04/11/shairport-emulator-cracks-open-the-door-for-more-unofficial-airp/") but I sure hope so.

---

