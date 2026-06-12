---
title: "No sound when playing .RM video files"
date: 2007-02-20
forum: Multimedia &amp; Video
---

### Post by barney_1 on 2007-02-20
Hi Folks,

I've been trying for a couple weeks to get this problem fixed but no dice.  So, here it goes:

Kubuntu 7.04 Feisty (development)
Kaffeine media player 0.8.3

I can play .RM (realvideo) files and see video perfectly but I have no sound.  I have tried installing the w32codecs, the xine-extracodecs, and several others.  

When I run kaffeine with this command:
```
kaffeine --verbose
```
I get this error when trying to play a .RM file:
```
xine: found demuxer plugin: RealMedia file demux plugin
video discontinuity #1, type is 0, disc_off 0
waiting for audio discontinuity #1
audio discontinuity #1, type is 0, disc_off 0
waiting for in_discontinuity update #1
vpts adjusted with prebuffer to 32967
load_plugins: plugin real will be used for video streamtype 39.
ffmpeg_audio_dec: increasing buffer to 98304 to avoid overflow.
load_plugins: plugin ffmpegaudio will be used for audio streamtype 21.
ffmpeg_audio_dec: unknown header with buf type 0x3210000
video_out_xv: VO_PROP_INTERLACED(0)
xine_play
[cook @ 0xb5966ad4]Necessary extradata missing!
ffmpeg_audio_dec: couldn't open decoder
audio_decoder: no plugin available to handle 'RealAudio COOK'

```

Any thoughts on how to correct this?

---

### Post by chggr on 2007-02-21
Try to use VLC.
This program has every codec you can imagine and it can play just anything.

---

### Post by NeoChaosX on 2007-02-24
I'm having this problem, too. It started happening in Feisty; in Edgy, Real files played audio just fine in Kaffeine as well. It was exactly like one problem I had a year ago when I couldn't get WMVs to play sound despite having w32codecs installed; it turns out I had to tweak ~/.xine/catalog.cache to get it to play sound. Maybe playing with that file again will get it working, but I'm not so sure.

chggr: I'd prefer not to use VLC for a number of reasons, one of which there are some format it actually doesn't support (I have a few videos encoded in Indeo v4, which it doesn't support). So fixing xine to get this working would be preferable.

ETA: Found a solution. Open up ~/.xine/catalog.cache in a text editor and find this section:
```
[/usr/lib/xine/plugins/1.1.4/xineplug_decode_real_audio.so]
size=11300
mtime=1171041406
type=131
api=15
id=realadec
version=10104
supported_types=52494336 52559872 52756480 
decoder_priority=5
```
Bump up the 'decoder_priority' value to 10. That should get audio with Real files working.

First scratchy sound in SDL games, now this. And Canonical smoothed out all my audio problems with Edgy...

---

### Post by barney_1 on 2007-02-24
Hey, great tip, Thanks!  I'm not on my Feisty box right now but can't wait to try it out.

As for the support not being there for Feisty, I would imagine that as it hits RC in April these things will get ironed out.  Hopefully this info can be useful for the developers.

---

### Post by yorick on 2007-03-09
Hi. I installed Feisty Herd 5 yesterday and was really bugged about this...

Thanks. This solution works. Has anyone opened a bug in Launchpad? We don't want this to creep into the final release... :)

---

### Post by danohuiginn on 2007-03-11
Related bug report in launchpad: [https://launchpad.net/ubuntu/+source/amarok/+bug/91500](https://launchpad.net/ubuntu/+source/amarok/+bug/91500)

---

### Post by barney_1 on 2007-03-13
Sorry folks, forgot to report back that this fixed my sound problems as well.

Say, I've never files a bug report.  Is there a how-to about it somewhere around here?  (I probably should have searched for one before asking, but oh well)

---

### Post by t_huankiat on 2007-04-21
> **NeoChaosX said:**
> 
```
[/usr/lib/xine/plugins/1.1.4/xineplug_decode_real_audio.so]
size=11300
mtime=1171041406
type=131
api=15
id=realadec
version=10104
supported_types=52494336 52559872 52756480 
decoder_priority=5
```
Bump up the 'decoder_priority' value to 10. That should get audio with Real files working.


Thanks man! The solution works like a charm!

---

### Post by pressman57 on 2007-04-24
This fixed gxine as well in xubuntu after a dist-upgrade.

---

### Post by Sweetrelease on 2007-04-29
Beautiful, i had this error and it was bugging me for the longest time. thank you so much for the post

---

### Post by tungah on 2007-05-26
I got Feisty and my ~/.xine/catalog.cache is empty... I'm kinda new to linux... Can someone help me? Thx!

---

### Post by qu9542 on 2007-05-27
It is a system/hidden folder wihich usually you will not see. In file manager you can enable an option to view them.

Anyway, what you can do is:

sudo gedit ~/.xine/catalog.cache

If your catalog.cache is empty, you need to install gxine first.
sudo apt-get install gxine

hope this help

---

### Post by george1984 on 2007-06-10
This was the only blemish in my Feisty-32 install. Could not solve it no-way.

Changing value from 5 to 10 worked instantly.

Grateful.

---

### Post by Ozztopia on 2007-11-12
I still use Feisty. The solution posted by NeoChaosX works perfectly. Now the .rmvb files play with video and audio. Thanks!!

---

