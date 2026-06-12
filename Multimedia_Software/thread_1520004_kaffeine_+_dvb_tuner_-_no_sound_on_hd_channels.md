---
title: "kaffeine + dvb tuner - no sound on hd channels"
date: 2010-06-29
forum: Multimedia Software
---

### Post by kristersaurus on 2010-06-29
Hey guys.

Finally got my tv tuner working with kaffeine and regular channels work just fine. However, HD streams are really choppy and have no sound. Anybody have any ideas? Some googling revealed something about increasing the number of audio and video buffers in a config file that does not exist on my machine ($HOME/.config/kde.org/Phonon-Xine.xine.conf). This is a hauppauge wintv-hvr 850 tuner, BTW.

Thanks for your time.

---

### Post by wonderingwhy on 2010-07-08
This is my exact same issue, HD streams are choppy and no sound. I'm using a Hauppauge WinTV-HVR-4000.

Thanks

---

### Post by torusturtle on 2010-10-01
On Ubuntu systems you can find the configuration file here:
```
~/.kde/share/apps/kaffeine/xine-config
```
It is working much better on my system with the settings
```
engine.buffers.audio_num_buffers:2000
engine.buffers.video_num_buffers:2500
```
watching HD Suisse.

---

### Post by giannib on 2010-12-29
Hi,

with new conf video is better, much more fluid, but still no sound.

btw. I would love to decode HD suisse....

---

### Post by vaxinator on 2011-01-27
This happens on my MSI Wind netbook, but not on my desktop PC. It is caused by insufficient processing power on my netbook, so video frames on HD channels get dropped and the audio drops out after a few seconds because it get so out of synch with the video frames. This happens with kaffeine and me-tv players.

The main problem is de-interlacing, it seems to need a lot of post-processing by the video engine. In Kaffeine turn de-interlacing off, you can do this from the playback/video menu, or you can modify the xine-config file: 
~/.kde/share/apps/kaffeine/xine-config

This should not cause a problem for progressive scan SD and HD channels, but interlaced channel streams will get jagged edges on moving objects in the video. 

One way I found to avoid this problem is to use the xine ui. It is faster than kaffeine and me-tv, but does not have a built-in channel scanner or epg display and is more difficult to setup, but if you want to try it there are install instructions here:

[http://www.linuxtv.org/wiki/index.php/Xine](http://www.linuxtv.org/wiki/index.php/Xine)

Remember to use the -X option with w_scan to make the channels.conf file.

After starting xine ui for the first time go to the options and set de-interlacing "on", it is set "off" by default. Also set the video driver to "xv" and sound driver to "Alsa" if you are still having playback problems.

If all this is still FAIL, then go buy a more powerful PC, goodluck.

---

### Post by wonderingwhy on 2012-05-17
Hi Chaps

I know this is an old post and therefore no-one maybe out there.

That said I have a question: How high can the audio buffers go re:

> engine.buffers.audio_num_buffers:2000 

I've set them to 2000 and no joy with the sound.

Interestingly I can record HDTV from Kaffeine, and play it back through VLC with sound.  What it feels like is that there's a box in Kaffeine that's been ticked for universal mute. The onscreen kaffeine speaker though clearly shows it's NOT muted.

---

