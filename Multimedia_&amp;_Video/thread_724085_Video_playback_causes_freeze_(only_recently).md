---
title: "Video playback causes freeze (only recently)"
date: 2008-03-14
forum: Multimedia &amp; Video
---

### Post by mikkyb on 2008-03-14
Hi All,

I have a problem with my video card on Ubuntu Gutsy 7.1. When I play a video, it will play for a while and eventually freeze. Sound will continue momentarily (up to 30 seconds) before stopping. However the mouse is still moveable after all this.

I have tried ctrl+alt+backspace/F1, searched high and low but nothing seems to work. 

The weird thing is that it didn't freeze when I was previously running Feisty.

The card is a Radeon 9200 Pro. I know it's old - and I'm about to buy a whole new system anyway, but I'd still like to figure out what the problem is just for the sake understanding.

This only occurs when I'm attempting to play a video, sometimes it will run for 5 minutes, sometimes only 5 seconds. I can sit around for hours working on my projects and doing lots of heavy compiling and I will never get a freeze unless I attempt to view a video.

Might be worth noting that Flash videos seem to work just fine, youtube has never caused a lock up.

I tried using the VESA driver just now, and I ran a video for 15 minutes before being satisfied that it wasn't going to freeze - but I was limited to only 800x600 resolution even though other resolutions were stated in the xorg.conf file.

It's odd that the video can play for a few minutes before a freeze no? This would indicate some sort of buffer overflow or something?

Unfortunately I've only been on Linux for a few months now so I'm not entirely sure what I should post in order to help diagnose the problem, so any direction would be appreciated.

---

### Post by -Phi- on 2008-06-09
I've had this start to happen too. I have an Intel video card, but otherwise the same behaviour. I open a video and the audio plays but the screen freezes other than my mouse. It doesn't seem to respond to keyboard or mouse input, so I have to hard reboot.

I'm running XFCE+Compiz Fusion and it happens independent of video player (I've tried mplayer, totem-gstreamer, and vlc).

Does anyone know where to start looking to debug?

- Phi

---

