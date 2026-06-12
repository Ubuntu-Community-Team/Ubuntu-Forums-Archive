---
title: "Amarok 1.4.5 can't play wma files"
date: 2007-05-24
forum: Multimedia &amp; Video
---

### Post by Baboontu on 2007-05-24
Hi
When I try to play wma files in Amarok 1.4.5 kde 3.5.7 feisty, i get an error concerning demuxing problem. I have win32 codecs installed and xine extra plugins. I used the xine-check tool and it gives me:
```
multiple xine executables found in your PATH
         I have found more than one occurance of 'xine' in your PATH:
         /usr/bin/X11/xine
         /usr/bin/xine
         You have probably installed xine-ui more than once, or the directory
         where you have installed xine occurs more than once in your PATH.
.......... unable to determine plugin directory......
```

Can someone help me please?

---

### Post by mitch.c on 2007-05-24
I am on Edgy, but my plugins path is: /usr/lib/xine/plugins/1.1.2/

You can use xine-config to find out where xine expects the plugins to be, and perhaps that will help you narrow down the problem.
```
$  xine-config --plugindir
  /usr/lib/xine/plugins/1.1.2
```
Are the libxine1-plugins or libxine packages installed

PS. It looks like the path on Feisty should be: usr/lib/xine/plugins/1.1.4/

---

### Post by Baboontu on 2007-05-24
Thanks for replying 
Yes, the plugins path is indeed "usr/lib/xine/plugins/1.1.4/" as you suggested. xine-check:
 ```
plugin directory /usr/lib/xine/plugins/1.1.4 exists
```
However :
```
xine-config executables have been found in these places:
         /usr/bin/X11/xine-config
         /usr/bin/xine-config
         This probably means you have several versions of xine-lib installed.
         It's probably best to uninstall all unused xine-libs.
         Further tests will use /usr/bin/X11/xine-config.
```
libxine1-plugins and libxine1 packages are installed.
still can't play wma...

---

### Post by mitch.c on 2007-05-24
> **Baboontu said:**
> 
```
xine-config executables have been found in these places:
         /usr/bin/X11/xine-config
         /usr/bin/xine-config
         This probably means you have several versions of xine-lib installed.
         It's probably best to uninstall all unused xine-libs.
         Further tests will use /usr/bin/X11/xine-config.
```
libxine1-plugins and libxine1 packages are installed.
still can't play wma...
I get the same messages, Amarok and xine work fine.

Where did you get the w32codecs? Are you sure they are installed? What is output of:
```
$ aptitude search w32codecs
```
Have you tried more than one wma file?

---

### Post by Baboontu on 2007-05-24
aptitude search w32codecs yields:

```
i   w32codecs                                        - win32 binary codecs
```
I think I've installed it through automatix.
I tried other wma and it played in Amarok. the problematic wmas played in CLI with mplayer :
```
ASF file format detected.
Invalid length in ASF header!
libavformat file format detected.

Forced audio codec: mad
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 44100 Hz, 2 ch, s16le, 128.0 kbit/9.07% (ratio: 16002->176400)
Selected audio codec: [ffwmav2] afm: ffmpeg (DivX audio v2 (FFmpeg))
```
but I was unable to play it with kmplayer:confused:

---

### Post by Baboontu on 2007-05-25
I think the problem is that these wmas files are DRM, right protected. but on a second thought, I could play them in Amarok in the past, because they appear on my playlist in [last.fm]("http://www.last.fm/") site.
Is it possible that Amarok changed something concerning  DRM capabilities? :confused:

---

