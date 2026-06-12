---
title: "no sound via HDMI with 9.04"
date: 2009-09-25
forum: Multimedia Software
---

### Post by royalwithcheese on 2009-09-25
Greetings, I am very new to Ubuntu, I'm running 9.04. I am using my TV as my monitor connected via HDMI cable. before installing Ubuntu I had the windows 7 release candidate running, with which the audio and video ran smoothly. However, since I've installed Ubunut (my setup hasn't changed) I have been unable to get the sound to go through the HDMI cable. 

When I connect head phones or traditional speakers through the stereo jack the sound plays, but I want the sound to come through my TV's speakers.

I've been through the comprehensive sound problem guide,  here is what I encountered:

the command
                                 [php]aplay -l [/php]gave me:                           [php]**** List of PLAYBACK Hardware Devices ****  
 card 0: NVidia [HDA NVidia], device 0: STAC92xx Analog [STAC92xx Analog]  
   Subdevices: 1/1  
   Subdevice #0: subdevice #0  
 card 0: NVidia [HDA NVidia], device 1: STAC92xx Digital [STAC92xx Digital]  
   Subdevices: 1/1  
   Subdevice #0: subdevice #0  
 card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]  
   Subdevices: 1/1  
   Subdevice #0: subdevice #0  
[/php]the command
[php]lspci -v[/php]               gave me (among many other things)
                          [php]00:07.0 Audio device: nVidia Corporation MCP78S [GeForce 8200] High Definition Audio (rev a1)  
     Subsystem: Elitegroup Computer Systems Device 2646  
     Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22  
     Memory at fbe78000 (32-bit, non-prefetchable) [size=16K]  
     Capabilities: <access denied>  
     Kernel driver in use: HDA Intel  
     Kernel modules: snd-hda-intel  
[/php]BUT, when I try
                                 [php]sudo modprobe snd-[/php] I get
                                 [php]FATAL: Module snd_ not found.[/php]
Additionally, I tried installing drivers using the "hardware drivers" application, but when I try to install them I am given a warning telling me I have held broken packages, when I go to the package manager, it says I don't have any broken packages. If I could get this application to work properly I feel as though it would solve my problem.



is there anyone out there who can help me get my audio to play through my hdmi cable? Are there known issues with Ubuntu and HDMI connectivity? would using an older version of Ubuntu (8.04 or 8.10 perhaps) yield better results?


here's my system details:
NVIDIA GeForce 8200
IDT 92HD206 8 channel
AMD Phenom 9600 quad core

---

### Post by andey on 2009-09-29
i have a similar issue, with
- Ubuntu 9.04
- ATI HD3850 -> DVI-HDMI Donggle -> LG 42' LCD

I installed the video drivers from ATI website, and video works correctly.
However, i cannot get any audio.

---

### Post by gordintoronto on 2009-09-29
I suggest you have a look at this thread:

[http://ubuntuforums.org/showthread.php?t=789578&highlight=howto+pulseaudio](http://ubuntuforums.org/showthread.php?t=789578&highlight=howto+pulseaudio)

---

### Post by royalwithcheese on 2009-09-29
I had success with the sound by following this article

[http://www.goingson.be/2008/12/ubuntu-and-hdmi-audio-output.html](http://www.goingson.be/2008/12/ubuntu-and-hdmi-audio-output.html)

The author uses 8.10 but I got it to work using 9.04

HOWEVER: although the sound works, the video driver screwed up my video output somewhat. the desktop no longer fills the screen and I get wierd flickering every time I open or close anything.

---

