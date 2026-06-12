---
title: "simultaneous midi apps playing"
date: 2011-01-13
forum: Multimedia Software
---

### Post by mutex77 on 2011-01-13
Howdy, 

Ive tried googling this but with all the info for alsa, pulseaudio and jack im a bit confused.....

I have a few applications that send output to a midi (timidity) port. Specifically im trying hydrogen and tuxguitar, although it seems to happen with any program that uses a midi out. 

When  I try to run them at the same time only 1 has sound. If I want to use midi with anything else I must exit that program. Ive tried using different midi ports for each app but that didnt seem to work. 

Is there a way around this? Is this what jack is for?

Regular audio apps like mp3 players can play at the same time as say a youtube video and seem to be full duplex. Its only when I access things that use midi that i have this problem. 

If anyone has any suggestions it'd save me alot of headaches. Id really like to use my metronome or drum machine with my guitar app!

---

### Post by mutex77 on 2011-01-25
Im answering my own question in case anyone was trying to do the same thing. 

Basically what I wanted to do was be able to play multiple midi apps at the same time. I use tuxguitar which uses midi, and a metronome which also uses midi. Having to exit one app to use another was a pain, but I wasnt sure if jack was the tool to do this. Not to mention where ALSA & PulseAudio fit into that. 

I got multiple midi apps working using jack, it allows you to route multiple apps to a single card. I have ALSA output to pulseaudio which handles all the other audio like media players and flash/youtube. The good news is I can literally start 3 midi apps, a media player and a youtube player at the same time. Not that you want to listen to 6 simultaneous streams, but you dont have to exit any app to hear it even if a player is paused in the background. 

I tried for hours and hours to get jack and pulse working. I wanted the output of jack to fed into the input of pulseaudio, which would allow me to use the pulse volume applet in gnome to control the volume of everything including midi. As far as I can tell, it doesnt work. But leaving pulseaudio and jack seperate works well, and is pretty seamless to the desktop environment once I installed another app to control the master volume and remove the pulseaudio volume control.

I hope this saves someone the frustration I had of trying to get it all to work!

---

