---
title: "Totem Youtube H264 ffdemux_swf error"
date: 2008-11-05
forum: Multimedia Software
---

### Post by Ashrael on 2008-11-05
Hi, I installed the youtube h264 plugin in totem ([http://www.soccio.it/michelinux/2008/03/29/h264-youtube-video-in-totem/en/](http://www.soccio.it/michelinux/2008/03/29/h264-youtube-video-in-totem/en/)) and it works on one system but fails on another??? 
This is what it says in totem: ffdemux_swf: Element doesn't implement handling of this stream. Please file a bug.
And started from terminal:
:~$ totem
** (totem:7813): DEBUG: Init of Python module
** (totem:7813): DEBUG: Registering Python plugin instance: YouTube+TotemPythonPlugin
** (totem:7813): DEBUG: Creating object of type YouTube+TotemPythonPlugin
** (totem:7813): DEBUG: Creating Python plugin instance
** (totem:7813): DEBUG: Init of Python module
** (totem:7813): DEBUG: Registering Python plugin instance: BBCViewer+TotemPythonPlugin
** (totem:7813): DEBUG: Creating object of type BBCViewer+TotemPythonPlugin
** (totem:7813): DEBUG: Creating Python plugin instance
** (totem:7813): DEBUG: Init of Python module
** (totem:7813): DEBUG: Registering Python plugin instance: YouTubeH264+TotemPythonPlugin
** (totem:7813): DEBUG: Creating object of type YouTubeH264+TotemPythonPlugin
** (totem:7813): DEBUG: Creating Python plugin instance
Traceback (most recent call last):
  File "/usr/lib/totem/plugins/youtubeh264/youtubeh264.py", line 117, in on_starting_video
    mrl = "http://www.youtube.com/get_video?video_id=" + urllib.quote (youtube_id) + "&t=" + urllib.quote (re.match (".*[?&]t=([^&]+)", location).groups ()[0]) +"&fmt=18"
AttributeError: 'NoneType' object has no attribute 'groups'
** Message: don't know how to handle application/x-shockwave-flash
** Message: Error: Element doesn't implement handling of this stream. Please file a bug.
gstffmpegdemux.c(1440): gst_ffmpegdemux_sink_activate_push (): /GstPlayBin:play/GstDecodeBin:decodebin0/ffdemux_swf:ffdemux_swf0:
failed to activate sinkpad in pull mode, push mode not implemented yet
I have not been able to find out why it works on one and fails on another system, but I hope anyone can give me a clue...
In the mean time I will investigate further...


TIA!

---

### Post by Ashrael on 2008-11-05
Oh and I forgot: totem does play youtube videos, just not h264...

TIA

---

### Post by Ashrael on 2008-11-20
Does anybody have a clue where i should look? 

please help.

---

### Post by HeWhoE on 2008-12-23
Try this.

Back up the original file, if you feel so inclined.
```
sudo mv /usr/lib/totem/plugins/youtubeh264/youtubeh264.py /usr/lib/totem/plugins/youtubeh264/youtubeh264.py_backup
```

Then move the attached file into the YouTube H264 plugin directory.
```
sudo mv youtubeh264.py /usr/lib/totem/plugins/youtubeh264/
```

---

### Post by keoni on 2009-01-04
This worked out perfectly for me although I did need to download the totem youtubeh264 plugin which is simple enough and then install this so thanks a lot!

---

### Post by Ashrael on 2009-01-17
I confirm! No more problems!

A BIG THANKS!

Ashrael

---

### Post by dodos on 2009-03-08
Hello, with your help now i solved the problem of ffdemux_swf error, but the videos that i play with H264 doesn't go in HQ but in normal/low quality....can u help me? thanks

sorry for my english :P

---

### Post by dodos on 2009-03-12
up

---

### Post by dodos on 2009-03-16
up up up

---

### Post by frogotronic on 2009-06-09
Yeah, solved the swf error, but now all videos in low quality...

---

