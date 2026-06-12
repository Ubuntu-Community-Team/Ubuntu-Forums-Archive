---
title: "Gstreamer's all messed up."
date: 2010-03-26
forum: Multimedia Software
---

### Post by maximus2010 on 2010-03-26
ok so im messing around with gtk+ and gstreamer to create a simple music player.


so my problem is that im trying to make gstreamer play a .mp3 file through the terminal via gst-tools and this is what i get.


```
gst-launch filesrc location= "file:///blahh/blah/blahh.mp3" ! mad  ! alsasink

WARNING: erroneous pipeline: no element "mad"
``````


gst-launch-0.10 playbin uri="file:///blahh/blahh/blah.mp3"
Setting pipeline to PAUSED ...
** Message: don't know how to handle application/x-id3
Pipeline is PREROLLING ...
ERROR: from element /GstPlayBin:playbin0/GstDecodeBin:decodebin0: A ID3 tag demuxer plugin is required to play this stream, but not installed.
Additional debug info:
gstdecodebin.c(986): close_pad_link (): /GstPlayBin:playbin0/GstDecodeBin:decodebin0:
No decoder to handle media type 'application/x-id3'
ERROR: pipeline doesn't want to preroll.
Setting pipeline to NULL ...
Freeing pipeline ...
```i don't know what to do :(

---

### Post by mc4man on 2010-03-26
works here as such
> 
doug@doug-desktop:~$ gst-launch filesrc location= "/home/doug/Desktop/test2/02 - Tears Of Rage.mp3"  ! mad  ! alsasink
Setting pipeline to PAUSED ...
Pipeline is PREROLLING ...
Pipeline is PREROLLED ...
Setting pipeline to PLAYING ...
New clock: GstAudioSinkClock


Maybe run this and see (the ugly is main one here for mp3

```
sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad \
gstreamer0.10-plugins-ugly
```

---

### Post by maximus2010 on 2010-03-27
> **mc4man said:**
> works here as such


Maybe run this and see (the ugly is main one here for mp3

```
sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad \
gstreamer0.10-plugins-ugly
```


I have all those installed and im still getting the same output

---

### Post by mc4man on 2010-03-27
> I have all those installed and im still getting the same output

Well I guess there may be no discounting what this means, possibly affected
> ok so im messing around with gtk+ and gstreamer

Otherwise assuming the plugin (ugly) and libmad0 are installed, maybe ck. the mp3('s).

does file /path/to/filename produce the expected info.

> doug@doug-desktop:~$ file '/home/doug/Desktop/test2/02 - Tears Of Rage.mp3' 
/home/doug/Desktop/test2/02 - Tears Of Rage.mp3: Audio file with ID3 version 2.3.0, contains: MPEG ADTS, layer III, v1, 128 kbps, 44.1 kHz, JntStereo

What if you install the gstreamer fluendo mp3 plugin and go 
Ex.
> gst-launch filesrc location= "/home/doug/Desktop/test2/02 - Tears Of Rage.mp3"  ! flump3dec  ! alsasink

---

### Post by maximus2010 on 2010-03-27
i checked the mp3 and it was fine and i installed fluendomp3 and tried

gst-launch filesrc location= '/home/dalton/Desktop/music/my_music/Evil Empire/Rage Against The Machine - Evil Empire - 01 - People Of The Sun.mp3' ! flump3dec ! alsasink 

and got 

WARNING: erroneous pipeline: no element "flump3dec"


maybe i have to update gstreamer somehow so it knows fluendo is installed

---

### Post by mc4man on 2010-03-27
I'm not really big on using gstreamer though do fool around with it a bit. It does seem something is amiss with your libs.

If you are on karmic (9.10), I'd suggest adding this ppa and getting new, updated gstreamer libs and plugins

[https://launchpad.net/~gstreamer-developers/+archive/ppa](https://launchpad.net/~gstreamer-developers/+archive/ppa)

(if you built gstreamer, probably should mention

I guess you could check out gst with this - (output is large so out putting to file in home

```
gst-inspect -p  > gst_output.log 2>&1
```


( also on karmic it sometimes doesn't hurt to restart

---

### Post by maximus2010 on 2010-03-28
> **mc4man said:**
> I'm not really big on using gstreamer though do fool around with it a bit. It does seem something is amiss with your libs.

If you are on karmic (9.10), I'd suggest adding this ppa and getting new, updated gstreamer libs and plugins

[https://launchpad.net/~gstreamer-developers/+archive/ppa]("https://launchpad.net/%7Egstreamer-developers/+archive/ppa")

(if you built gstreamer, probably should mention

I guess you could check out gst with this - (output is large so out putting to file in home

```
gst-inspect -p  > gst_output.log 2>&1
```( also on karmic it sometimes doesn't hurt to restart



I have to be the biggest idiot ever , i forgot i compiled gstreamer from source when i started messing around with it. so everything i installed wasn't working right. i uninstalled it and installed tools and good,bad etc form synaptic and everything works fine.

---

