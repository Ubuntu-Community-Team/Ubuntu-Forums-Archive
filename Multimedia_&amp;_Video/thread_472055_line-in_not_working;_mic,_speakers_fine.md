---
title: "line-in not working; mic, speakers fine"
date: 2007-06-12
forum: Multimedia &amp; Video
---

### Post by marquarc on 2007-06-12
I have two computers with the same problem, one laptop and one desktop. So I can only assume it's some simple configuration issue that I have overlooked. For simplicity's sake, I'm just going to post info relating to this laptop -- if I get one working, I'm sure the other will follow shortly. Though I guess it should be mentioned that the other sound card is a Sound Blaster Live! Value. 

Simply put, all sound features(playback, mic recording) seem to work just fine except for recording via line-in -- which is very important to me.  Ubuntu detects my sound card just fine during installation.

lspci says:
00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 02)
        Subsystem: Cirrus Logic Crystal WMD Audio Codec
        Flags: bus master, medium devsel, latency 0, IRQ 5
        I/O ports at d800 [size=256]
        I/O ports at dc80 [size=64]

I've been trying to record on both Audacity and GnuSound. Same problem in both. I've selected Line-In Capture in Volume Control, and I get no signal. I've selected it with alsamixer, and the same problem arises. Nothing is muted (that I can see), and all the volumes, if not maxed, are certainly high enough to at least see a signal if one were present. In Audacity, the options for selecting a recording device are: 
OSS /dev/dsp
ALSA: sound card (hw:0,0)
ALSA: sound card - MIC ADC (hw:0,1)
ALSA: front
ALSA: iec958
ALSA: spdif

While I get slightly different levels of quality, Microphone recording works with all of those, provided I have it selected in Volume Control, and have the microphone plugged into the correct port. Similarly, Line-In doesn't work with a single one of those settings, so I'm led to believe that what I choose in Audacity really doesn't matter much.

I think this is the big clue, though: In alsamixer, when I look at the Capture settings, Line, Aux, CD, etc, do not have the bar graphs that Mic has. I will attempt to attach a screenshot, as I have trouble describing that in words. But I think this may be indicative of Ubuntu not recognizing that I do, in fact, have a line-in port on my sound card. If that's the case, how can I get Ubuntu to recognize line-in?

I'm a musician, and I'm interested in using Linux to do my recording. I've dabbled in Linux here and there, but I've never become much of an expert. Usually I can fiddle around and get things going, but I've been working on this problem for almost a week, and it's got me pulling my hair out. The microphone port just won't be good enough if I plan on doing any serious recording. Any help would be greatly appreciated. 

Thanks,
Corey

PS - in case my attachment doesn't work, here's the url for a screenshot of alsamixer: [http://i152.photobucket.com/albums/s171/plasticus/temp/alsamixer-nolinein.jpg](http://i152.photobucket.com/albums/s171/plasticus/temp/alsamixer-nolinein.jpg)

Edit: I suppose it should be noted that I'm running Ubuntu 7.04

---

### Post by mgdell on 2007-06-21
I have exactly the same problem with my new Dell machine.  :( 

Someone please help!  :) 

-Mike

---

### Post by flerchjj on 2007-06-21
Wow same problem on new Dell bought with 7.04 installed. 
This is a **very** critical problem to me.

Please help. Thanks in advance.

---

### Post by flerchjj on 2007-06-22
Don't like posting immediately after myself, but I wanted to make sure notification was sent out.

I'm still playing with it, but it looks like the audio lines are all mis-routed for ALSA on my new Dell Dimension E520 that came with Ubuntu 7.04.  The ALSA Line was routed to the Rear Mic (Pink), the ALSA Front Mic was routed to the Front Mic, and the ALSA Rear Mic was routed to the Stereo Output Rear Channel (Black)... go figure.

The easiest way I've found to test inputs with ALSA (assuming your speakers work) is to open the terminal & type 
```
arecord | aplay
```
This will route your currently selected ALSA input (from the Volume Control aka ALSA Mixer) to the speakers.  You can then move from audio jack to audio jack with your input to find where ALSA is reading from.

Maybe the desktop has the same issue as mine and the inputs are being read incorrectly.  Sound quality isn't that great yet (hear ~16kHz tones occasionally).

---

### Post by tgalati4 on 2007-06-22
Most modern sound cards have assignable inputs and outputs.  They can be swapped and moved around.  I'm not sure if there is a standard, but it's possible that you need to reassign your ports.  I'm not sure how to go about it, but I know the drivers in Windows allows you to remap the channels.

If this is a dual-boot machine, set the channel mapping as needed in Windows, then test it in Linux.  If you have a Linux-only machine, then try moving the plugs around until you discover the mapping.

---

