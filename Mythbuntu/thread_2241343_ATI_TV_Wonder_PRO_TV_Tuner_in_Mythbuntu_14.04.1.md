---
title: "ATI TV Wonder PRO TV Tuner in Mythbuntu 14.04.1"
date: 2014-08-25
forum: Mythbuntu
---

### Post by Sega dude on 2014-08-25
I have an old ATI TV Wonder Pro TV Tuner I would like to get working with Mythbuntu 14.04.1.  According to [this]("http://www.mythtv.org/wiki/ATI_TV-Wonder") page, the card is compatible with Linux. Can someone walk me through getting this card working? Your help would be greatly appreciated.

---

### Post by TheFu on 2014-08-25
old ATI Wonder cards used the bt chips for analog TV. Most of the world has switched to digital signals - so that card will only work with analog TV inputs ... perhaps from an old VCR.

Regardless - to get any real help, you need to provide the chip used by the card. Linux doesn't usually care about brand names - just the chips actually used.  If it is a PCI tuner, use **lspci** to learn more.

If you are planning to really setup MythTV to be useful, then the HDHR4 for OTA/ATSC signals is a great choice and for CableCARD needs, the HDHR-Prime is worth consideration. These are networked tuners, not PCI based, which means they can be used by any computer on the network.   Oh - I don't think the CableCARD-based tuners will work with Linux - thanks to the DRM content folks - only Windows is supported with the DRM drivers.

---

### Post by Sega dude on 2014-08-26
Here's what lspci -v says about the card:

> 02:00.0 Multimedia video controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
	Subsystem: Advanced Micro Devices, Inc. [AMD/ATI] ATI TV Wonder Pro
	Flags: bus master, medium devsel, latency 20, IRQ 16
	Memory at fc000000 (32-bit, non-prefetchable) [size=16M]
	Capabilities: [44] Vital Product Data
	Capabilities: [4c] Power Management version 2
	Kernel driver in use: cx8800


I got a bit farther with it, MythUbuntu sees the card as /dev/video0. But I don't know how to set it up as a capture card so that I can scan for channels and watch tv from the MythTV frontend. What do I have to select on the capture card setup screen? If I could get help with that, it would be great. When I had this card working under Windows it was able to get channels from my cable TV connection no problem.

---

### Post by TheFu on 2014-08-26
[http://www.linuxtv.org/wiki/index.php/Conexant_CX2388x](http://www.linuxtv.org/wiki/index.php/Conexant_CX2388x) says that chip is for analog TV. That doesn't exist in the USA anymore and I suspect it doesn't exist in most of the world.

Cable TV here is digital - QAM. The card is not. Further, cable TV here is only encrypted, so clear-QAM tuners don't work at all any more. I remember the day that happened and have since switched over to ATSC tuners with antennas in the attic.

Exactly what TV do you expect to watch?  The only input that will work is from an RCA-yellow cable - about 360i resolution.

---

### Post by ronniepinsky on 2014-09-10
> **TheFu said:**
> [http://www.linuxtv.org/wiki/index.php/Conexant_CX2388x](http://www.linuxtv.org/wiki/index.php/Conexant_CX2388x) says that chip is for analog TV. That doesn't exist in the USA anymore and I suspect it doesn't exist in most of the world.

Cable TV here is digital - QAM. The card is not. Further, cable TV here is only encrypted, so clear-QAM tuners don't work at all any more. I remember the day that happened and have since switched over to ATSC tuners with antennas in the attic.

Exactly what TV do you expect to watch?  The only input that will work is from an RCA-yellow cable - about 360i resolution.

[/rant]
How about try to actually help with the problem?  What does it matter what your personal cable configuration is?  This is hard, boring work, and the last thing we need is you telling us all the reasons it supposedly won't work.

Millions of people in the United States still receive analog cable broadcasts.  It's either a choice between that, going without TV, or getting an expensive cable company box.  Digital OTA TV does not work in real life.
[/rant]

I just went through getting these set up again.  I used a dual tuner system with these from 2009-2010 with mythtv on Debian with no problems once it was set up.

Challenges we have with this card right now:
1.  Reception.  Being in a place that still receives analog cable or over the air broadcasts.

2.  Wear and tear.  The cards are physically getting old and things like capacitors may be wearing out.  One of my two cards does not work at all anymore and can only tune to a green screen.

3.  Audio issues
A.  Analog sound capture (line in, working in 2009-10 host hardware: nvidia nforce 2)
Pulseaudio - Line-in and microphone capture rarely works.  This results in (usually) no analog sound from the card.  I can make it work temporarily as follows:
1.  Mute line-in/set all volume levels to max/switch capture device to line-in
2.  Set mythbackend capture card audio device to "ALSA:plughw:0,0"
3.  Start mythfrontend and watch live tv
4.  Start audacity and record a few seconds from from device: "NVidia nForce 2: - (hw:0,0): Line:0"
5.  Leave live tv
6.  Enter live tv
7.  Leave tive tv
8.  Enter live tv  - proper audio should be working
B.  Digital sound capture (cx88-alsa module, also working in 2009-10) - 
This module is not loaded at startup and modprobing it causes it to fail to create an ALSA device.  This results in no digital sound from the card.
Alsa - **Working fine once you remove the garbage that is pulseaudio**

4.  Memory usage.  The documentation claims that with 512MB of RAM you can watch 2 streams at once.  This may have used to be possible, but now this system almost is struggling with one stream.

5.  Confusing interface.  There are at least 2 channel frequency settings.

6.  Poor Documentation.  It seems like documentation was actually better a few years ago.  There is almost no ATI TV wonder information out there.  Doing a search for "mythtv audio" "mythtv sound" "mythbuntu audio" "mythbuntu sound" - these possibly relevant pages come up:
[http://www.mythtv.org/wiki/PCI_TV_audio](http://www.mythtv.org/wiki/PCI_TV_audio) - PCI audio wiki page - says this does not work on "cheaper" cards but this card was not cheap when new, and it used to work anyway.  So now you get to feel bad about having something "cheap" when it's really just bad programming causing the problem.
[http://www.mythtv.org/wiki/Sound_Troubleshooting](http://www.mythtv.org/wiki/Sound_Troubleshooting) - Sound fixes wiki pages - Is stunningly short and unhelpful.

Time wasters on this project:
Bad memory stick (fix: replace) - 1 hour
Bad tuner card hardware (fix: replace) - 2 hours
Pulseaudio bugs (fix: removal) - 10 hours
General Settings channel frequency problem (fix: set to us-cable instead of us-bcast) - 2 hours

It is working like it used to now though.

---

