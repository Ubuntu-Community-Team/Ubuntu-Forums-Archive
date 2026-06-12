---
title: "ACC/MP4 problem with gstreamer [all plugins installed]"
date: 2007-05-27
forum: Multimedia &amp; Video
---

### Post by kounavi on 2007-05-27
Hello, I am sorry if this has already been answered, I looked as hard as I could, but could not find an *answer* that helped.


I have an .m4a audio file that works just fine in VLC and Mplayer. 

But I'm having trouble playing it with any music player.

First of all, Totem says there are some codecs missing, I say OK, next next, it shows some list of (3) codecs that should be installed. Guess what? They already are installed, so OK/Apply next next gives me an error saying there's no available decoder (see attachments).
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=33618[/IMG]
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=33619[/IMG]


The problem is that neither banshee nor any other player I've tried plays the files (xmms, bmp)


Here's the file output 
```
01 Upside Down.m4a: ISO Media, MPEG v4 system, iTunes AAC-LC
```

So I tried uninstalling all gstreamer plugins just in case something is broken

```
apt-get remove --purge gstreamer0.10-plugins*
```

and then reinstalled them  (plus everything that got uninstalled before) 


The same...

So all I got is the totem messages from when i ran it from the terminal:
```

** Message: don't know how to handle audio/mpeg, mpegversion=(int)4, framed=(boolean)true, codec_data=(buffer)1210, rate=(int)44100, channels=(int)2
** Message: Error: You do not have a decoder installed to handle this file. You might need to install the necessary plugins.
gstplaybasebin.c(2182): prepare_output (): /play

** Message: Missing plugin: gstreamer.net|0.10|totem|MPEG-4 AAC decoder|decoder-audio/mpeg, mpegversion=(int)4, framed=(boolean)true (MPEG-4 AAC decoder)

** (gnome-codec-install:3265): WARNING **: return value of custom widget handler was not a GtkWidget
/usr/lib/python2.5/site-packages/AppInstall/AppInstall.py:1532: GtkWarning: gtk_tree_model_sort_sort: assertion `tree_model_sort->default_sort_func != NULL' failed
  item.applications.set_default_sort_func(None)
/usr/lib/python2.5/site-packages/AppInstall/AppInstall.py:1118: GtkWarning: gtk_tree_model_sort_sort: assertion `tree_model_sort->default_sort_func != NULL' failed
  model.set_default_sort_func(None)
additional codec installation declined
** Message: don't know how to handle audio/mpeg, mpegversion=(int)4, framed=(boolean)true, codec_data=(buffer)1210, rate=(int)44100, channels=(int)2
** Message: Error: You do not have a decoder installed to handle this file. You might need to install the necessary plugins.
gstplaybasebin.c(2182): prepare_output (): /play

** Message: Missing plugin: gstreamer.net|0.10|totem|MPEG-4 AAC decoder|decoder-audio/mpeg, mpegversion=(int)4, framed=(boolean)true (ignoring)
** Message: All missing plugins are blacklisted, doing nothing

```

That was totem trying to play the file, trying to install the extra codecs, and me clicking ok/next etc.


Any ideas?

xmms errors: 
```
libmp4ff.so.0: cannot open shared object file: No such file or directory
```

banshee seems to find the file OK when importing (see attachment) but when I click on playback I get an error (decoder error once again). [ the first one on the list, I 've just tried to play it, the second is just imported, when I try to play that too, I get the same error]
[img]http://ubuntuforums.org/attachment.php?attachmentid=33622[/img]


so that i get this straight:

```
dpkg -l | grep mp4
ii  bmp-mp4                                    2.0.0+cvs20040908+mp4v2+bmp-0ubuntu3   a mp4/aac audio player for bmp
ii  faad                                       2.0.0+cvs20040908+mp4v2+bmp-0ubuntu3   freeware Advanced Audio Decoder player
ii  libmp4v2-0                                 2.0.0+cvs20040908+mp4v2+bmp-0ubuntu3   MP4 container library - runtime files
ii  xmms-mp4                                   2.0.0+cvs20040908+mp4v2+bmp-0ubuntu3   a mp4/aac audio player for xmms


 dpkg -l | grep gstreamer0.10-plug
ii  gstreamer0.10-plugins-bad                  0.10.4-1ubuntu1                        GStreamer plugins from the "bad" set
ii  gstreamer0.10-plugins-bad-dbg              0.10.4-1ubuntu1                        GStreamer plugins from the "bad" set
ii  gstreamer0.10-plugins-bad-doc              0.10.4-1ubuntu1                        GStreamer documentation for plugins from the
ii  gstreamer0.10-plugins-bad-multiverse       0.10.4-3                               GStreamer plugins from the "bad" set (Multiv
ii  gstreamer0.10-plugins-bad-multiverse-dbg   0.10.4-3                               GStreamer plugins from the "bad" set (Multiv
ii  gstreamer0.10-plugins-base                 0.10.12-0ubuntu1                       GStreamer plugins from the "base" set
ii  gstreamer0.10-plugins-base-apps            0.10.12-0ubuntu1                       GStreamer helper programs from the "base" se
ii  gstreamer0.10-plugins-base-dbg             0.10.12-0ubuntu1                       GStreamer plugins from the "base" set
ii  gstreamer0.10-plugins-base-doc             0.10.12-0ubuntu1                       GStreamer documentation for plugins from the
ii  gstreamer0.10-plugins-farsight             0.10.2-1ubuntu2                        Gstreamer plugins for audio/video conferenci
ii  gstreamer0.10-plugins-good                 0.10.5-1ubuntu2                        GStreamer plugins from the "good" set
ii  gstreamer0.10-plugins-good-dbg             0.10.5-1ubuntu2                        GStreamer plugins from the "good" set
ii  gstreamer0.10-plugins-good-doc             0.10.5-1ubuntu2                        GStreamer documentation for plugins from the
ii  gstreamer0.10-plugins-ugly                 0.10.5-0ubuntu2                        GStreamer plugins from the "ugly" set
ii  gstreamer0.10-plugins-ugly-dbg             0.10.5-0ubuntu2                        GStreamer plugins from the "ugly" set
ii  gstreamer0.10-plugins-ugly-doc             0.10.5-0ubuntu2                        GStreamer documentation for plugins from the
ii  gstreamer0.10-plugins-ugly-multiverse      0.10.5-2                               GStreamer plugins from the "ugly" set (Multi
ii  gstreamer0.10-plugins-ugly-multiverse-dbg  0.10.5-2                               GStreamer plugins from the "ugly" set (Multi

```



I am an advanced linux user and google usually does the work for me, but I'm stuck here.
Any ideas will be welcome.


Thank you very much in advance.


I'm sorry for the large images and the poor english

---

### Post by kounavi on 2007-06-03
nobody? 
:(

---

### Post by diebels on 2007-06-03
Try gstreamer0.10-pitfdll with w32codecs from [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com)

---

### Post by mhacleth on 2007-11-28
Hi,
I was having the same problem as yours. In my course of searching for a solution, I came across a post that deals with this.

The solution was to install libfaad2-0

This package contains the libmp4ff.so.0 that is needed by Banshee, Rhythmbox, and Exaile to play m4a files. :-)

Install the one in the official ubuntu repository. 

Hope this helps.

---

