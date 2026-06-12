---
title: "vlc when playing on fullscreen heats up my laptop &amp; then crashes"
date: 2010-03-01
forum: Multimedia Software
---

### Post by dosox on 2010-03-01
I can't play videos on fullscreen with VLC player for more than 7 to 8 minutes.
It heats up my laptop & then CRASHED... help?

[Compaq c785tu, 2 GB Ram, Ubuntu 9.10]

---

### Post by no2498 on 2010-03-02
go to system preferences multimedia systems selector 
click video,set the plugin to,  x window system (no xv)

or if you dont have that setup yet
open a terminal type ( gstreamer-properties ) click enter
click video,set the plugin to,  x window system (no xv)
hope this helps

it did work for me on a desk top
a dell with 910 ubuntu

---

### Post by Yellow Pasque on 2010-03-03
So is it your CPU or GPU overheating?

---

### Post by sam.reader on 2010-03-03
VLC is a powerful player which utilizes the maximum of the CPU. Try to un-check most of the video rendering options that you will find the in the video settings of the player.
I think this might be due to the use of multiple video and audio decoders at the same time.
Check and reply back.

---

### Post by dosox on 2010-03-03
> **no2498 said:**
> go to system preferences multimedia systems selector 
click video,set the plugin to,  x window system (no xv)

or if you dont have that setup yet
open a terminal type ( gstreamer-properties ) click enter
click video,set the plugin to,  x window system (no xv)
hope this helps

it did work for me on a desk top
a dell with 910 ubuntu
  
Ahh I think it works :) Thanks

@Temüjin CPU

---

