---
title: "Dell XPS M1210 SPDIF Digital Output not working"
date: 2008-08-07
forum: Multimedia Software
---

### Post by Helipil0t on 2008-08-07
So I have just about everything working perfectly on my Dell M1210 this seems to be the only thing that I can't figure out.  

So heres the problem.  I can play audio through my laptop speakers just fine but the Dell XPS M1210 has a digital output that requires an adapter to plug into an "s-video" type plug.  This adapter splits to three plugs.  One S-Video, One Composite Video and one RC Audio connection(digital output).  Works great in WinXP or Vista.  all I usually have to do is switch the default audio device to digital and it works.  

It seems to not be the case in Ubuntu. :(  The digital device is detected as seen using:

sean@sean-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

I tried going to System>Preferences>Sound under the Devices tab and selected STAC92xx Digital as the device for sound playback.  But that doesn't seem to work.  When I test it I can't hear any audio but my system still plays audio through my analog speakers when I try Amarok.  

Has anyone else successfully used their SPDIF audio output in Ubuntu with an XPS M1210 or similar laptop?  

I'd appreciate any help I can get. 

Thanks

---

### Post by geopteryx on 2008-08-14
Hi,

I have the same problem on DELL Inspiron 9400: I cannot get my SPDIF-Output working. It works fine under XP/Vista but not with Ubuntu 8.04.
I have been trying everything since 4 days, but it does not help. It seems to be a big problem, since much people are reporting troubles about SPDIF.

***
sebastien@INSPIRON:~$ amixer
Simple mixer control 'Master',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 22 [71%] [-13.50dB] [on]
  Front Right: Playback 22 [71%] [-13.50dB] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 182 [71%] [-14.60dB]
  Front Right: Playback 182 [71%] [-14.60dB]
Simple mixer control 'LFE',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 22 [71%] [-13.50dB] [on]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'IEC958 Default PCM',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 15
  Front Left: Capture 11 [73%] [16.50dB] [off]
  Front Right: Capture 11 [73%] [16.50dB] [off]
Simple mixer control 'Capture Mux',0
  Capabilities: volume
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 4
  Front Left: 2 [50%] [20.00dB]
  Front Right: 2 [50%] [20.00dB]
Simple mixer control 'Digital',0
  Capabilities: cvolume
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 120
  Front Left: Capture 0 [0%] [-30.00dB]
  Front Right: Capture 0 [0%] [-30.00dB]
Simple mixer control 'Input Source',0
  Capabilities: cenum
  Items: 'Mic'
  Item0: 'Mic'

***

But you may try to configure your ALSA-driver adding this two lines at the bottom of your alsa-base file:

type:
sudo nano /etc/modprobe.d/alsa-base

and insert:

alias snd-card-0 snd-hda-intel
options snd-hda-intel model=dell-m82

at the bottom of the file.

For me, it did not make any difference ("model=dell-m27"), but you may be more lucky...

Here my config: [http://pastebin.ca/1171251](http://pastebin.ca/1171251)

Any help is welcome!

---

### Post by Helipil0t on 2008-08-14
Well I'm glad to hear I'm not the only one having problems getting my SPDIF working.  I tried what you suggested and it didn't help me either.  Thanks for you're input.

---

### Post by Helipil0t on 2009-06-06
Well this was driving me nutts for the past year and I finally figured it out.  Through some more research and clicking around I found the solution.  check out the following post for Ubuntu 8.04. 

[http://ubuntuforums.org/showthread.php?t=916809](http://ubuntuforums.org/showthread.php?t=916809)

I've since moved on to Ubuntu 9.04 and the solution is very similar. 
Click on your volume icon in the top panel and click Volume Control...

In the Device drop-down menu select Sigmatel STAC9221 A1 (OSS Mixer)  (or similar if you have a different setup)

Now Select Preferences and you should see Digital-1 Playback.  Put a check mark in the box and voilla!!!  Crank up the volume and enjoy the tunes!!  To test go to System>Preferences>Sound  Make sure you select HDA Intel STAC92xx Digital (ALSA) and click the Test Button.

You'll notice that you won't get audio from your browser or audio events.  To fix that run alsamixer in the terminal and crank up your PCM channel.  

Can't believe it took me this long to figure it out. I feel like such an idiot. :P

---

