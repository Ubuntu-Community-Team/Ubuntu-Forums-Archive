---
title: "Microphone suddenly doesn't work in skype"
date: 2010-09-15
forum: Multimedia Software
---

### Post by Heuvelgek on 2010-09-15
First off, yes I know there already are a lot of threads concerning this problem, but not a single problem is similiar to mine. 

So, here goes. 

My audio and video used to work great in skype. Two days ago connected my laptop and TV, in order to use the TV as a second monitor, to watch a football match (I only have IPTV). Only thing I had to do was to go to System -> Preferences -> Sound and switch (in the hardware tab) my Internal Audio Hardware from Analog Stereo Duplex to Digital Stereo (HDMI) Output + Analog Stereo Input.

So after the match I switched it back to Analog Stereo Duplex and proceeded to skype with my girlfriend. Problem was, the mic stopped working. It works just fine in 'Input' tab of my sound preferences, as well as in sound recorder. She, in skype, heard nothing but static. Test call doesn't work either. 

Now I've done all the usual stuff, Skype isn't allowed to automatically adjust mixer levels and my mic is already boosted. I've reinstalled skype and everything. I'm running out of ideas. 

Hardware info as well as amixer info below:

 *-multimedia
             description: Audio device
             product: 82801I (ICH9 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:22 memory:d4500000-d4503fff




Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 64
  Mono: Playback 33 [52%] [-23.25dB] [on]
Simple mixer control 'Headphone',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 64 [100%] [0.00dB] [on]
  Front Right: Playback 64 [100%] [0.00dB] [on]
Simple mixer control 'Speaker',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 64 [100%] [0.00dB] [on]
  Front Right: Playback 64 [100%] [0.00dB] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 252 [99%] [0.60dB]
  Front Right: Playback 252 [99%] [0.60dB]
Simple mixer control 'Front Mic',0
  Capabilities: cvolume penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 3
  Front Left: Capture 0 [0%] [0.00dB]
  Front Right: Capture 0 [0%] [0.00dB]
Simple mixer control 'Mic',0
  Capabilities: cvolume penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 3
  Front Left: Capture 3 [100%] [30.00dB]
  Front Right: Capture 3 [100%] [30.00dB]
Simple mixer control 'Mic Jack Mode',0
  Capabilities: enum
  Items: 'Mic In' 'Line In'
  Item0: 'Mic In'
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 15
  Front Left: Capture 15 [100%] [22.50dB] [on]
  Front Right: Capture 15 [100%] [22.50dB] [on]
Simple mixer control 'PC Beep',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 3
  Mono: Playback 0 [0%] [-18.00dB] [off]

---

### Post by prshah on 2010-09-15
> **Heuvelgek said:**
> I switched it back to Analog Stereo Duplex and proceeded to skype with my girlfriend.

In Volume Icon->"Sound Preferences"->"Input" Tab there will be a list of input-capable devices (Eg your webcam's mic). Select each one, raise the volume to approx 75% and proceed to say something ("testing, testing"?) and see if the volume meter registers anything.

You should also check audio settings in Skype: "S" button->options->Sound devices->Microphone should be set to "PulseAudio (local)"

Please post back if the problems still persist.

---

### Post by Heuvelgek on 2010-09-15
Thanks for the reply. 

I did and checked all those things already. In my Sound Preferences there is only one device for sound input - that one device i have selected - and two connectors: Line in and Microphone. I have tried both, although it goes without saying that Microphone is the one to select. On the input level meter the microphone works and everything. 

All my skype sound devices are already set to PulseAudio (local), as I cannot select anything else. 

I have also installed the PulseAudio device chooser, after I encountered the problem, but I can;t really make sense of it, so I haven't changed anything there.

---

### Post by Heuvelgek on 2010-09-15
Bump, I'm really at a loss here. Don't want to spend another 4 hours reinstalling Windows 7 just because of skype. Had enough trouble with that damned program already.

---

### Post by ntamas on 2010-12-05
I found the following work around which is still a bit annoying. 
I start up my computer then open skype. Microphone doesn't work.
I set the microphone to line-in then back to microphone. Then I restart skype.
Everything is fine.
The question is why is it necessary.

---

### Post by ExemplarUbuntu on 2010-12-06
I am having similar problems following an upgrade of Ubuntu.

[http://ubuntuforums.org/showthread.php?t=1622224&highlight=skype+pulseaudio](http://ubuntuforums.org/showthread.php?t=1622224&highlight=skype+pulseaudio)

---

