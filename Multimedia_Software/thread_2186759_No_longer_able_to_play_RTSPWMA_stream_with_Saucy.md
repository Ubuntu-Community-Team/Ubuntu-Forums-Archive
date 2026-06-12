---
title: "No longer able to play RTSP/WMA stream with Saucy"
date: 2013-11-08
forum: Multimedia Software
---

### Post by matthew1429 on 2013-11-08
I used to be able to use VLC to play streaming links like [http://www.blueletterbible.org/audio_video/courson_jon/Gen/w/W3001.asx](http://www.blueletterbible.org/audio_video/courson_jon/Gen/w/W3001.asx)

As you will see it downloads an ASX file which I used to be able to double click on to play the streaming media. If you actually download the above file, you'd see that it's just a wrapper for streamed audio via rtsp/wma

<ASX Version = "3.0">
<ENTRY>
<TITLE>Genesis 1</TITLE>
<REF HREF = "rtsp://stream.blueletterbible.org/courson_jon/Gen/W3001.wma" />
<AUTHOR>Jon Courson</AUTHOR>
</ENTRY>
</ASX>

In older versions of Ubuntu, I could play the asx file & could paste the above URL into the open network stream in VLC and successfully listen to the stream.

Now since I've upgraded to Ubuntu 13.10 where the medibuntu package is no longer maintained, I cannot listen on VLC, Totem, or any other player for that matter. If I open VLC from the terminal I get the following report:[0xb5307248] live555 demux error: Broken packet detected (300 vs 0 or 300 + 628 vs 631)

Can anyone help?

---

### Post by monkeybrain20122 on 2013-11-09
Your link doesn't work, gives 404 not found error.

---

### Post by matthew1429 on 2013-11-09
fixed

---

### Post by mc4man on 2013-11-09
Vlc probably has something broken or different with live555, see same errors here with vlc 2.1.1 & your link. 
However it plays ok in mplayer (using a month old or so mplayer), has a few warnings but works
> 
mplayer rtsp://stream.blueletterbible.org/courson_jon/Gen/W3001.wma
...........
[lavf] stream 0: audio (wmavoice), -aid 0
Clip info:
 title: Genesis 1 - W3001
 artist: Jon Courson
 copyright: © 1997 Jon Courson
 WMFSDKNeeded: 0.0.0.0000
 DeviceConformanceTemplate: S1
 WMFSDKVersion: 9.00.00.2980
 IsVBR: 0
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
libavcodec version 55.34.100 (internal)
AUDIO: 16000 Hz, 1 ch, floatle, 16.0 kbit/3.12% (ratio: 2000->64000)
Selected audio codec: [ffwmavoice] afm: ffmpeg (WMA Voice audio (FFmpeg))
==========================================================================
[AO OSS] audio_setup: Can't open audio device /dev/dsp: No such file or directory
AO: [alsa] 16000Hz 1ch floatle (4 bytes per sample)
Video: no video
Starting playback...



---

### Post by matthew1429 on 2013-11-09
thanks for your reply - this may be an alternate mplayer issue but this is my output after fixing the ip6 issue

MPlayer svn r34540 (Ubuntu), built with gcc-4.7 (C) 2000-2012 MPlayer Team

Playing rtsp://stream.blueletterbible.org/courson_jon/Gen/W3001.wma.
Resolving stream.blueletterbible.org for AF_INET...
Connecting to server stream.blueletterbible.org[64.58.178.156]: 554...
Resolving stream.blueletterbible.org for AF_INET...
Connecting to server stream.blueletterbible.org[64.58.178.156]: 80...

Server returned 404: Not Found
No stream found to handle url rtsp://stream.blueletterbible.org/courson_jon/Gen/W3001.wma

---

### Post by mc4man on 2013-11-09
> **matthew1429 said:**
> thanks for your reply - this may be an alternate mplayer issue but this is my output after fixing the ip6 issue

MPlayer svn r34540 (Ubuntu), built with gcc-4.7 (C) 2000-2012 MPlayer Team

 
Probably just the repo versions of mplayer are old & use an old libav libraires

here I have a newer version that uses FFmpeg (internal), though for the build didn't enable live555 thru liblivemedia

> doug@doug-Lenovo-IdeaPad-Y580:~$ mplayer
MPlayer SVN-r[COLOR="#0000CD"]36461[/COLOR] (C) 2000-2012 MPlayer Team


---

### Post by matthew1429 on 2013-11-09
still getting 404 errors :(

---

### Post by matthew1429 on 2013-11-10
any help would be greatly appreciated

---

### Post by matthew1429 on 2013-11-10
I solved this issue - unsure what the problem is with VLC but was able to get mplayer working by changing the rtsp:// in the above link to mms:// and it works like a charm

---

