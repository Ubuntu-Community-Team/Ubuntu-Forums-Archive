---
title: "MP3 playback missing after Skype Installation"
date: 2008-10-25
forum: Multimedia Software
---

### Post by altima on 2008-10-25
[THE PROBLEM IS SOLVED]

hello everyone!
It's been my second day with ubuntu (the version is hardy). I like it very much but I was missing Skype. So I started looking for the possible ways to install it.
my system is 64-bit, so I tried different sophisticated recipes posted all over the net to get the 32-bit version of skype running. but then I found the 64-bit version and seamlessly installed it. now it works fine but none of the players (Totem, Rhythmbox) starts playback. Rhythmbox even freezes and has to be force quit. audio-files on the internet pages either as sound in youtube video don't work, too, but LastFM works. as for VideoLAN, it simply doesn't produce any sound but seems to be playing the file. that's so weird and I am afraid I will have to reinstall the system, because I still know nothing about linux except apt-get command. I installed it to my laptop because it recognized all the devices immediately (which was a big problem for ms-windows). 
my volume control preferences say there are several devices - 
HDA Intel (alsa mixer), 
Sigmatel Stac 9228 (OSS Mixer), 
Playback Alsa PCM on front:0 (STAC 92xx Analog) via DMA (Pulseaudio mixer), 
Capture Monitor Source of Alsa PCM on front:0 (STAC 92xx Analog) via DMA (Pulseaudio mixer) 
and Capture Alsa PCM on front:0 (STAC 92xx Analog) via DMA (Pulseaudio mixer).
I don't understand what happened. could anybody help me please?

 [http://ubuntuforums.org/showthread.php?t=780354&highlight=skype+sound](http://ubuntuforums.org/showthread.php?t=780354&highlight=skype+sound)


The solution was to install PulseAudio from [here]("https://wiki.ubuntu.com/PulseAudio"). I found link to the page [here]("http://ubuntuforums.org/showpost.php?p=6035564&postcount=3")

---

### Post by Stochastic on 2008-10-25
> **altima said:**
> now {skype} works fine but none of the players (Totem, Rhythmbox) starts playback. Rhythmbox even freezes and has to be force quit. 

Just to clarify, do you have Skype running (in the tray) while you're trying these tasks or have you quite Skype and still see these effects?  I think this issue may stem from Skype improperly hogging the audio device.

---

### Post by altima on 2008-10-26
it doesn't depend on that, unfortunately. the mp3-s just don't play.

---

### Post by altima on 2008-10-26
and by the way, I have reinstalled ubuntu but the problem's left. =((((

---

### Post by altima on 2008-10-26
I installed RealPlayer - it works. But nothing else does.

---

