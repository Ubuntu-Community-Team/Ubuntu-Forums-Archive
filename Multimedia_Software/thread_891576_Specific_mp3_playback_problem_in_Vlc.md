---
title: "Specific mp3 playback problem in Vlc"
date: 2008-08-16
forum: Multimedia Software
---

### Post by slaabrockband on 2008-08-16
Dejavue:
 I have uninstalled totemplayer, still got vlc and Rhymthbox.
 Mp3 playblack is fine in Rhymthbox... but choppy and not optimal in Vlc.

Vlc is favorite player for all purpose - 
I have just upgraded from 7.10 to Ubuntu 8.04 via a clean install - and
right now I can't identify and get rid of that irritating bugger. 

Looking for hints and help.

---

### Post by adept_king on 2008-08-30
[http://forum.videolan.org/viewtopic.php?f=13&t=46701&p=151845&hilit=alsa+pulseaudio#p151845](http://forum.videolan.org/viewtopic.php?f=13&t=46701&p=151845&hilit=alsa+pulseaudio#p151845)

this worked for me.  not sure if this is a fix or if pulseaudio will try to start on reboot. 

it said: go into System/Preferences/Sound and select alsa to be the default playback engine for music and sound.
then if neccessary, go to terminal and enter: killall pulseaudio

---

