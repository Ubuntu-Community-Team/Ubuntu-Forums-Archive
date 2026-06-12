---
title: "For those who're able to play Internet radio in Hardy, how do you do it?"
date: 2008-05-10
forum: Multimedia Software
---

### Post by boomtisk on 2008-05-10
Hardy is working alright for me so far, but the one problem I haven't been able to fix so far is my apparent inability to play Internet radio streams in every application I tried, including Rhythmbox, Quod Libet, Exaile and Totem. Even the stations that are listed in Rhythmbox by default won't play, no matter if they use a pls or m3u playlist. I can play normal mp3s fine.

I read the Multimedia Howto and enabled the medibuntu repos, but nothing really seemed to work. Does anyone know what packages are required for listening to streaming audio so I can check if I have them installed? Lots of thanks in advance.

Oh, yeah, every time I start Rhythmbox, I'm told the Magnatune and Jamendo plugins cannot be started, I guess this might just be related to the problem.

---

### Post by boomtisk on 2008-05-10
Let's try a bump. Strangely enough, my other installation of Hardy on my desktop computer (Ubuntu Studio) plays Internet radio just fine and doesn't give me the plugin errors, either.

---

### Post by stream303 on 2008-05-10
For an ogg fan like myself, it seems that the latest Hardy updates place the ogg decoder into the "good" gstreamer so Totem works for me when listening to ogg streams again.

[www.hbr1.com](www.hbr1.com) used to be included in older ubuntu playlists, so I still use them occasionally.

Actually what I do is just do it from the cli - I download the pls file, nab the url from inside it, and play it with ogg123 (download vorbis-tools first)

For example, to listen to an ambient stream from them:
```
ogg123 http://radio.hbr1.com:19800/ambient.ogg
```

---

### Post by boomtisk on 2008-05-10
> **stream303 said:**
> For an ogg fan like myself, it seems that the latest Hardy updates place the ogg decoder into the "good" gstreamer so Totem works for me when listening to ogg streams again.

[www.hbr1.com](www.hbr1.com) used to be included in older ubuntu playlists, so I still use them occasionally.

Actually what I do is just do it from the cli - I download the pls file, nab the url from inside it, and play it with ogg123 (download vorbis-tools first)

For example, to listen to an ambient stream from them:
```
ogg123 http://radio.hbr1.com:19800/ambient.ogg
```

Thanks for the tip, looks like "nabbing" the URL from the m3u/pls file lets me listen to streams again. :)

But still, it's pretty weird that gstreamer seems to hate playlist files now.

For some added fun, here's the error messages Rhythmbox vomits out when I run it in a terminal:

> 
(rhythmbox:5350): Rhythmbox-WARNING **: Unable to grab media player keys: Could not get owner of name 'org.gnome.SettingsDaemon': no such name
Traceback (most recent call last):
  File "/usr/lib/rhythmbox/plugins/jamendo/__init__.py", line 28, in <module>
    from JamendoSource import JamendoSource
  File "/usr/lib/rhythmbox/plugins/jamendo/JamendoSource.py", line 37, in <module>
    jamendo_song_info_uri = gnomevfs.URI("http://img.jamendo.com/data/dbdump.en.xml.gz")
TypeError: could not parse URI

(rhythmbox:5350): Rhythmbox-WARNING **: Could not load plugin jamendo


(rhythmbox:5350): Rhythmbox-WARNING **: Error, impossible to activate plugin 'Jamendo'
Traceback (most recent call last):
  File "/usr/lib/rhythmbox/plugins/magnatune/__init__.py", line 32, in <module>
    from MagnatuneSource import MagnatuneSource
  File "/usr/lib/rhythmbox/plugins/magnatune/MagnatuneSource.py", line 43, in <module>
    magnatune_song_info_uri = gnomevfs.URI("http://magnatune.com/info/song_info_xml.zip")
TypeError: could not parse URI

(rhythmbox:5350): Rhythmbox-WARNING **: Could not load plugin magnatune


(rhythmbox:5350): Rhythmbox-WARNING **: Error, impossible to activate plugin 'Magnatune Store'

(rhythmbox:5350): Rhythmbox-WARNING **: Could not open device /dev/radio0
** Message: don't know how to handle text/uri-list
Rhythmbox-Message: Missing plugin: gstreamer|0.10|rhythmbox|text/uri-list decoder|decoder-text/uri-list

(rhythmbox:5350): GLib-GObject-WARNING **: invalid uninstantiatable type `(null)' in cast to `GstMiniObject'

(rhythmbox:5350): GStreamer-CRITICAL **: gst_mini_object_unref: assertion `mini_object->refcount > 0' failed
no application found
Rhythmbox-Message: No installation candidate for missing plugins found.

---

### Post by mixtri on 2008-05-18
Your best bet is to follow this guide found on the Ubuntu beginner talk area under Multimedia category.

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683) :)

---

### Post by ssam on 2008-08-07
this is due to missing packages. see
[https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/255884](https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/255884)

---

