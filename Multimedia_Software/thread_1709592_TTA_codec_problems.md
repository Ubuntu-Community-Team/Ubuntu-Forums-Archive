---
title: "TTA codec problems"
date: 2011-03-18
forum: Multimedia Software
---

### Post by Tidus Zero on 2011-03-18
When I try playing any TTA files in Clementine, Rhythmbox or Movie Player all I hear is white noise. It plays normally in VLC and SMPlayer, but I want to be able to play TTA files in Clementine. I've been able to do so before I recently reinstalled Ubuntu 10.10 on my computer.

I've tried installing ttaenc-3.4.1 from source, and nothing  changed. I also tried installing ffmpeg-0.6.1 from source, but that  didn't help either.

SMPlayer file properties
 ```

General
   [COLOR=#000000]File: [/COLOR][COLOR=#000000]/home/user/Music/audio.tta[/COLOR]
   [COLOR=#000000]Size[/COLOR][COLOR=#000000]: 325744 KB (318 MB)[/COLOR]
   [COLOR=#000000]Length:[/COLOR][COLOR=#000000] 00:41:58[/COLOR]
   [COLOR=#000000]Demuxer:[/COLOR][COLOR=#000000] lavf[/COLOR]

[COLOR=#000000]Initial Audio Stream[/COLOR]
   [COLOR=#000000]Format[/COLOR][COLOR=#000000]: TTA1[/COLOR]
   [COLOR=#000000]Bitrate[/COLOR][COLOR=#000000]: 0 kbps[/COLOR]
   [COLOR=#000000]Rate[/COLOR][COLOR=#000000]: 44100 Hz[/COLOR]
   [COLOR=#000000]Channels:[/COLOR][COLOR=#000000] 2[/COLOR]
   [COLOR=#000000]Selected codec[/COLOR][COLOR=#000000]: fftta[/COLOR]
```If anyone can help, that'd be great.

---

### Post by shantiq on 2011-03-18
ok are you sure you fully installed  ttaenc?

when you run ttaenc in your terminal you get

```
~$ ttaenc
TTA1 lossless audio encoder/decoder, release 3.4.1
Copyright (c) 2007 Aleksander Djuric. All rights reserved.
For more information see http://tta.sourceforge.net
------------------------------------------------------------
usage:	ttaenc [command] [options] file(s).. <output path/>

------------------------------------------------------------
commands:
------------------------------------------------------------
	-e	encode file(s)
	-d	decode file(s)
	-t	test file(s)
	-o name	specify output file name
	-v	show codec version
	-h	this help
------------------------------------------------------------
options:
------------------------------------------------------------
	-x	wave-extensible output file format
	-u	delete source file if successful
------------------------------------------------------------
when file is '-', use standard input/output.


```

i have just checked clementine, mplayer and all fine so i am thinking it could just be the codec itself not running fully


it is a weird one ttaenc to install since one does not configure

simply open attached codec with extract here place it in home folder then


```
make 

```
```
sudo make install
```
then run    ```
ttaenc
``` to make sure then try clementine again


:KS:KS  if you already done all this then i don't know:KS

---

### Post by mc4man on 2011-03-18
None of the players you mentioned should have an issue decoding .tta
Also none use ttaenc - vlc and mplayer use libavcodec, gstreamer players use the gstreamer bad plugin.
If you wished a better set of gstreamer libs and plugins for lucid or maverick then I'd add this ppa, 
[https://launchpad.net/~gstreamer-developers/+archive/ppa](https://launchpad.net/~gstreamer-developers/+archive/ppa)

(and make sure you have the gstreamer bad, ugly and ffmpeg plugins installed

No repo packaged player or plugin is going to use a built ffmpeg unless you built it as shared, and doing that can cause some issues

---

### Post by shantiq on 2011-03-19
> **mc4man said:**
> None of the players you mentioned should have an issue decoding .tta
Also none use ttaenc - vlc and mplayer use libavcodec, gstreamer players use the gstreamer bad plugin.
If you wished a better set of gstreamer libs and plugins for lucid or maverick then I'd add this ppa, 
[https://launchpad.net/~gstreamer-developers/+archive/ppa](https://launchpad.net/~gstreamer-developers/+archive/ppa)

(and make sure you have the gstreamer bad, ugly and ffmpeg plugins installed

No repo packaged player or plugin is going to use a built ffmpeg unless you built it as shared, and doing that can cause some issues


ok so maybe forget all i said:KS

---

### Post by Tidus Zero on 2011-03-19
> **mc4man said:**
> None of the players you mentioned should have an issue decoding .tta
Also none use ttaenc - vlc and mplayer use libavcodec, gstreamer players use the gstreamer bad plugin.
If you wished a better set of gstreamer libs and plugins for lucid or maverick then I'd add this ppa, 
[https://launchpad.net/~gstreamer-developers/+archive/ppa]("https://launchpad.net/%7Egstreamer-developers/+archive/ppa")

(and make sure you have the gstreamer bad, ugly and ffmpeg plugins installed

No repo packaged player or plugin is going to use a built ffmpeg unless you built it as shared, and doing that can cause some issues
I added the repository and upgraded them.
```

gstreamer0.10-ffmpeg                      version 0.10.11-1
gstreamer0.10-plugins-ugly                version 0.10.17-1~maverick1
gstreamer0.10-plugins-bad                 version 0.10.21-1~maverick1
gstreamer0.10-plugins-bad-multiverse      version 0.10.20-1ubuntu1

```It still plays white noise though.

---

