---
title: "no sound when play video/audio with xine"
date: 2008-08-31
forum: Multimedia Software
---

### Post by pxhai on 2008-08-31
First, my system (hardy) works ok, until now I use Mplayer to play. I have almost plugin/codec/etc: gstreamer, w32codecs ... installed. I like the interface of xine-ui, so I install xine. It can play every files I want, but without sound. Help plz, any idea will be appreciated.

---

### Post by pxhai on 2008-09-01
I found the solution:
open file:  ~/.xine/config
change the following line:

#audio.pulseaudio_device:    -->  audio.pulseaudio_device: pulseaudio

and it works!

You can also specify the default volume at startup:

#audio.volume.mixer_volume   -->  audio.volume.mixer_volume:100
#audio.volume.remember_volume    -->   audio.volume.remember_volume:1

---

### Post by vemon on 2009-05-11
Just wanted to thank you for posting back your solution. This is exactly how it should go :). I hate people posting up questions but leaving out the answer when they eventually find it.

---

