---
title: "Microphone Fixed"
date: 2008-03-13
forum: Multimedia &amp; Video
---

### Post by earth_consumer on 2008-03-13
System:Dell PowerEdge 400C, 2.8GHz Server/Desktop
OS: Ubuntu Gutsy 7.10 iso burn distro,  default
The problem: Sound works, Mic not working with gnome-sound-recorder 2.20.1 or Skype Ver. 1.4.0.118

I found the solution was posted in the following blog: the blog screen shots are 7.04 I think

[http://10xforce.blogspot.com/2007/06/ubuntu-microphone-problems-and.html](http://10xforce.blogspot.com/2007/06/ubuntu-microphone-problems-and.html)

1) Double click the volume icon next to date on gnome desktop, this opens Volume Control Intel ICH5 (Alsa Mixer)
2) Click Switches tab,... if Captiure and Mic Boost are missing go on to #3, if not ????
3) Click Playback tab, 
4) Use edit-->preferences to get to the check boxes
5) Make sure Microphone, Microphone Capture and Microphone Boost boxes are checked
6) Click close and Exit .. If you want you can check Switches tab for the features before exit.

Notes: You may have to enable it each time you reboot. I have to check and possibly fix. Not sure yet.  I hope this helps some folks. 

Here's a screen shot of my gnome (GUI) dialog windows for Gutsy 7.10, 

[img]http://i216.photobucket.com/albums/cc69/earth_consumer/Micfix.jpg[/img]

---

### Post by xc3RnbFO8P on 2008-03-14
Can you show the hole list of Volume Contol Preferences.
You should check all capture, (and uncheck Mic boost for now)

---

### Post by earth_consumer on 2008-03-14
> **Ringi said:**
> Can you show the hole list of Volume Contol Preferences.
You should check all capture, (and uncheck Mic boost for now)

The solution above is the simplest method for the Ubuntu 7.10 beginner.  But if you must see and or adjust other settings... open the Terminal and run "alsamixer".  Here's a couple of screen shots.


[img]http://i216.photobucket.com/albums/cc69/earth_consumer/alsamixT1.jpg[/img]

[img]http://i216.photobucket.com/albums/cc69/earth_consumer/alsamixT2.jpg[/img]

---

### Post by xc3RnbFO8P on 2008-03-14
I mean Volume Contol Preferences, see screenshot.

---

### Post by earth_consumer on 2008-03-21
Ringi, Sorry for the delay.

Here is a list of my 7.10
Volume Control Preferences

Master
Master Mono
Master Surround
Headphone jack Sense
PCM
Surround
Surround jack Mode
Center
LFE
Line-in
Line-in Capture
Line Jack sense
CD
CD Capture
Microphone
Microphone Capture
Mic Boost (+20dB)
Mic Select
Video
Phone
Phone Capture
Aux
Aux Capture
Capture
Mix
Mix Mono
Channel Mode
Downmix
Exchange Front/Surround
External Amplifier
High Pass Filter Enable
Spread Front to Surround and Center/LFE
Stereo Mic
V_REOUT Enable

---

