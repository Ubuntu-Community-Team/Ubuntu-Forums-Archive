---
title: "Asus M4A78LT-M, Audio Setup (output to headphone jack and digital at same time)"
date: 2011-09-24
forum: Multimedia Software
---

### Post by FitzGerald_F on 2011-09-24
Hello All, 
About a month ago, I installed Linux on a new desktop PC (my first install).  The only issues I had were with the video driver and audio.  This post is about the audio.  It appears that Ubuntu is very functional as a basic desktop PC for my families needs (unfortunately games are a bit dicier, especially newer games).  

Here is my configuration: 
Motherboard - Asus M4A78LT-M (I believe this is a 760g)
CPU - Athlon II X2 250 
I am using the integrated graphics and sound.  
The audio appears as "HDA ATI SB: VIA VT1708S"
There is a HDMI port but I don't have that enabled (can't remember I disabled in the BIOS or not.  

Basically on my old Windows XP (not this configuration), I was able to hear sound out of both the headphone jack and my receiver (through the SPDIF).  I'm having trouble configuring Ubuntu 11.04 (64-bit) to do the same.  

Using the "DigitalOUT Alsa Wiki" ([http://alsa.opensrc.org/DigitalOut](http://alsa.opensrc.org/DigitalOut)) I've pretty much confirmed that it is possible for me to get sound through digital (in a digital passthrough) and I can get sound through my  headphones.  If I direct aplay through the various hardware devices.    

So it looks like primarily my audio is set by "Sound Preferences".  My  hardware profile is currently "Analog Stereo Output" because it doesn't  appear like there is a profile for "Digital Stereo (ICE958) + Analog  Stereo Output", although I *do see* a hardware profile of "Digital  Stereo (ICE958) + Analog Stereo Input".  By changing these settings I  can toggle between the headphone jack, and the output on my receiver  (not sure if it is digital).  

Using the various mixers I have installed doesn't seem to help me.  For some reason out of the box "alsamixer" didn't appear to be really functional (after going through updates it seems to work now).  I installed "galsa", which was even worse and I wasn't even able to enable my digital through a radial button.  The useful GUI Mixer appeared to be "GNOME Alsa Mixer", I was able to actually check my ICE958 to turn it on (although I don't hear sound even with it checked, so even some functionality is broken, I think it is due to the fact that my hardware profile is set up for the headphones via above paragraph).  

So it's true, setting up audio is utterly confusing in Ubuntu.  I've been able to get by for a month since I don't care, and have audio through my headphone jack.  I'm asking for some help in getting this all setup so that I hear sound through my headphones, and the receiver (and it is digital when appropriate to the receiver) at the same time.

---

