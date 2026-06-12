---
title: "alsa and zoom"
date: 2022-11-05
forum: Multimedia Software
---

### Post by lich444 on 2022-11-05
I am using  [COLOR=#000000]Ubuntu [/COLOR]**20.04.5 LTS    ** Focal Fossa[B]  instaalled a thied party software ZOOM 
in the instalition was some sugestion about instaling Alsa  as this computer  is 6-8 year old and was using  winwows 10 for short time because ubuntu 16 would not installed  itself 
I finaly instaled ububtu 16 xxx  abd make many upgrade 
Questions :  /
1  how canIi check if Alsa is installed on computer
2  can i use Zoom to its full capacity  w/o Alsa
3  /how to install Alsa
4 any better software  then Alsa 
5. a usb Dynamiv microphone  Matter?
Eli[/B]

---

### Post by Holger_Gehrke on 2022-11-05
ALSA - The Advanced Linux Sound Architecture - is a set of drivers (part of the kernel) and a set of utility programs for communicating with those drivers which is the default sound system on Linux. It should be installed by default, at least it always was for me on any Ubuntu since 12.04.

[LIST=1]
[*]To get information on the state of ALSA you can run 'alsa-info' from the command line. This script will gather information about your ALSA installation, write them to a file and (optionally) upload them to alsa.org. 'alsa-info' is part of the package alsa-utils which should have been installed during system installation. 
[*]Since I have never used Zoom, I can't tell you anything about it. But I suspect that it's not that ALSA is missing but that there's a sound-server - probably pulse-audio - running and doesn't allow Zoom to take direct control of the sound hardware through ALSA. It's generally considered very bad form to try to do this, you're supposed to connect to the sound server and make your requests to that so that all programs can play or record sound and not just the one that got control of the hardware. If that's the problem you might be able to make pulse-audio get out of the way by using pasuspender ('pasuspender -- [COLOR=#006400]name-of-the-executable-for zoom[/COLOR]'; replace the green part with the actual path and name of the executable file for Zoom). 
[*]As i already said, ALSA is part of the default installation. On my system, the following packages have 'alsa' in their name: alsa-base, alsa-utils, alsa-topology-conf, and alsa-ucm-conf. You could do a 'sudo apt install alsa-base alsa-topology-conf alsa-ucm-conf alsa-utils' from the command line to install these packages, but they should already be installed. 
[*]There are things ALSA either doesn't do or doesn't do well enough. For these things we have sound servers like pulse-audio, JACK or pipewire which sit on top of ALSA. 
[*]Depends on what you mean with 'matters'. Normally a USB microphone would be seen by the kernel as a USB-soundcard without outputs and with one input. But if there's no driver for the chip(s) used in the microphone in ALSA, then you'll get no input from the microphone. 
[/LIST]

Holger

---

