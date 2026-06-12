---
title: "Mplayer Audio / OSS / USB audio no worky"
date: 2009-05-02
forum: Multimedia Software
---

### Post by Controls_Nut on 2009-05-02
Hi all,

First off, I just spent most of the night building a new desktop and installing Ubuntu 9.04 :) . After getting a few things out of the way, I tried to get my usb stereo (a philips az2555) working with linux. Well, it does work, but not with what I want it to :(. The stereo shows up as a Philips UAC3553B usb audio device. So here is the problem:

I would like the usb stereo to work with Mplayer/KMplayer, I have demonstrated it works with Kaffeine and totem movie player. However, to get it to work, I have to have "Philips UAC3553B USB Audio (OSS)" selected in "Preferences >> Sounds >> Music and Movies", otherwise the annoying sound test defaults to the head-phone/audio outputs on the computer. So:

With Kaffeine I have to set the audio configuration to oss to get it to work. It saves my setting, but I have to change it from oss to something different and then back to oss every time I open Kaffeine, otherwise it defaults to playing on the headphone connections. 

Totem, works with the USB no problem. Just wish it was a bit more full-featured.

Mplayer/KMplayer - I can set the audio driver to OSS for both of these, but then I get no sound from anything, headphones or usb device. There are no problems playing sound via the computer headphone jacks when something (like ALSA) is selected though.

Well, that about sums it up. If anyone can help me figure out how to get the OSS or USB working with Mplayer it would be much appreciated. Brownie points if someone can tell me how to prioritise the USB device over the desktop audio, so I don't have switch Kaffeine's settings everytime.

Thanks!

Nick

P.S.

I did restart playback or the player after changing the audio settings each time, I'm fairly confident that isn't the issue.

---

### Post by Ricco on 2010-03-06
I have the exact same problem. Totem can play the sound but is not very good with the video or subtitles. SMplayer is the other way around.
It's the same with the Firefox-plugins. And flash like Youtube doesn't work with usb-audio either.
I have seen a few other threads with more people with this problem but I haven't found a solution anywere yet.

---

