---
title: "Playing RAM (RealAudio Media) files"
date: 2013-01-04
forum: Multimedia Software
---

### Post by Lars Noodén on 2013-01-04
I haven't seen RAM files since the early days of the web.  How can they be played on modern Ubuntu systems?  Here is a sample of files:
[http://www.otr.net/?p=lone](http://www.otr.net/?p=lone)

Edit: It may be called 'RealPlayer' now.

---

### Post by ron999 on 2013-01-04
> **Lars Noodén said:**
> I haven't seen RAM files since the early days of the web.  How can they be played on modern Ubuntu systems?
Hi
Here's an example...
Download the ram file with wget:-
```
wget http://www.otr.net/r/lone/1.ram
```
 
Open it with gedit/leafpad/etc and look inside:-
> rtsp://www.otr.net/28.8/lone - The Lone Ranger/lone.19--.--.--_Lone_Pine.rm?title="Lone Pine"&author="The Lone Ranger"&copyright="OTR.Network"

Choose the part *in front of the question mark*:-
**rtsp://www.otr.net/28.8/lone - The Lone Ranger/lone.19--.--.--_Lone_Pine.rm**

Play it with MPlayer:-
```
mplayer "rtsp://www.otr.net/28.8/lone - The Lone Ranger/lone.19--.--.--_Lone_Pine.rm"
```

Or download it with MPlayer:-
```
mplayer -bandwidth 9999999 "rtsp://www.otr.net/28.8/lone - The Lone Ranger/lone.19--.--.--_Lone_Pine.rm" -dumpstream -dumpfile Lone_Pine.rm
```

---

### Post by Lars Noodén on 2013-01-04
Thanks.  I tried VLC first but that didn't seem to work with rtsp://

I tried both mplayer examples you have and both give the error 'Exiting... (End of file)' without any result.  Would ffmpeg or avconv be able to handle that ancient a format?

---

### Post by andrew.46 on 2013-01-04
MPlayer will play the links directly with the -playlist option:

```

andrew@skamandros~$**[COLOR="Red"] mplayer -playlist http://www.otr.net/r/lone/1.ram[/COLOR]**
Resolving www.otr.net for AF_INET6...

Couldn't resolve name for AF_INET6: www.otr.net
Resolving www.otr.net for AF_INET...
Connecting to server www.otr.net[66.90.77.10]: 80...

Cache size set to 320 KBytes
MPlayer SVN-r35710-4.7.2 (C) 2000-2012 MPlayer Team

Playing rtsp://www.otr.net/28.8/lone - The Lone Ranger/lone.19--.--.--_Lone_Pine.rm?title="Lone Pine"&author="The Lone Ranger"&copyright="OTR.Network".
Resolving www.otr.net for AF_INET6...

Couldn't resolve name for AF_INET6: www.otr.net
Resolving www.otr.net for AF_INET...
Connecting to server www.otr.net[66.90.77.10]: 554...

Cache size set to 320 KBytes
Cache fill: 17.50% (57344 bytes)   

libavformat version 54.50.102 (internal)
REAL file format detected.
Stream description: Audio Stream
Stream mimetype: audio/x-pn-realaudio
[real] Audio stream found, -aid 0
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
libavcodec version 54.81.100 (internal)
[sipr @ 0xf67700]Invalid block_align: 320. Mode 16k guessed based on bitrate: 16000
AUDIO: 16000 Hz, 1 ch, floatle, 16.0 kbit/3.12% (ratio: 2000->64000)
**[COLOR="Red"]Selected audio codec: [ffsipr] afm: ffmpeg (FFmpeg Sipr/Acelp.net audio)[/COLOR]**
==========================================================================
AO: [oss] 16000Hz 1ch s16le (2 bytes per sample)
Video: no video

A:  19.6 (19.5) of 1186.0 (19:46.0)  0.1% 16% 

```

Seems like a very slow stream from my end of the world... I believe too that Real Audio sipr is a less commonly found in Real Media files.

---

### Post by ron999 on 2013-01-04
> **Lars Noodén said:**
> I tried both mplayer examples you have and both give the error 'Exiting... (End of file)' without any result

```
@ubuntu:~$ mplayer "rtsp://www.otr.net/28.8/lone - The Lone Ranger/lone.19--.--.--_Lone_Pine.rm"
MPlayer SVN-r35707-4.5.2 (C) 2000-2012 MPlayer Team

Playing rtsp://www.otr.net/28.8/lone - The Lone Ranger/lone.19--.--.--_Lone_Pine.rm.
Resolving www.otr.net for AF_INET6...

Couldn't resolve name for AF_INET6: www.otr.net
Resolving www.otr.net for AF_INET...
Connecting to server www.otr.net[66.90.77.10]: 554...

Cache size set to 640 KBytes
Cache fill: 18.75% (122880 bytes)   

libavformat version 54.49.102 (internal)
REAL file format detected.
Stream description: Audio Stream
Stream mimetype: audio/x-pn-realaudio
[real] Audio stream found, -aid 0
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
libavcodec version 54.81.100 (internal)
[sipr @ 0x8d167a0]Invalid block_align: 320. Mode 16k guessed based on bitrate: 16000
AUDIO: 16000 Hz, 1 ch, floatle, 16.0 kbit/3.12% (ratio: 2000->64000)
Selected audio codec: [ffsipr] afm: ffmpeg (FFmpeg Sipr/Acelp.net audio)
==========================================================================
[AO OSS] audio_setup: Can't open audio device /dev/dsp: No such file or directory
AO: [alsa] 16000Hz 1ch floatle (4 bytes per sample)
Video: no video
Starting playback...
A:   0.0 (00.0) of 1186.0 (19:46.0)  0.3% 19%  
```

---

### Post by Lars Noodén on 2013-01-04
Ok.  Thanks.  I got it playing.  Now I have to figure out how to filter the audio to improve it.

---

### Post by ron999 on 2013-01-04
> **Lars Noodén said:**
> ... Now I have to figure out how to filter the audio to improve it.
Good luck with that, kemosabe. :p

---

### Post by bob-linux-user on 2013-01-04
According to Wikipedia there is a linux version of Real Player based on Helix. I have no personal experience of it, just something i googled.

---

### Post by shantiq on 2013-01-05
> **bob-linux-user said:**
> According to Wikipedia there is a linux version of Real Player based on Helix. I have no personal experience of it, just something i googled.


i tried that  a couple of times for fun; but it was no fun as [for me] it did not work at all:KS

---

