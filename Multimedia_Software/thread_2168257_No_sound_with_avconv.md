---
title: "No sound with avconv"
date: 2013-08-17
forum: Multimedia Software
---

### Post by Sworddragon on 2013-08-17
Trying to record the sound from alsa with avconv results in a file which doesn't play any sound. Here is the output from the recording:

```
sworddragon@ubuntu:~$ avconv -f alsa -i hw:0 /tmp/test.mkv
avconv version 0.8.6-6:0.8.6-1ubuntu2, Copyright (c) 2000-2013 the Libav developers
  built on Mar 30 2013 22:20:06 with gcc 4.7.2
[alsa @ 0x111c280] Estimating duration from bitrate, this may be inaccurate
Input #0, alsa, from 'hw:0':
  Duration: N/A, start: 60726.233173, bitrate: N/A
    Stream #0.0: Audio: pcm_s16le, 48000 Hz, 2 channels, s16, 1536 kb/s
Output #0, matroska, to '/tmp/test.mkv':
  Metadata:
    encoder         : Lavf53.21.1
    Stream #0.0: Audio: libvorbis, 48000 Hz, 2 channels, s16
Stream mapping:
  Stream #0:0 -> #0:0 (pcm_s16le -> libvorbis)
Press ctrl-c to stop encoding
^Csize=     121kB time=11.16 bitrate=  88.5kbits/s    
video:0kB audio:113kB global headers:4kB muxing overhead 3.553759%
Received signal 2: terminating.
```

It seems to record something also I'm having only one soundchip:

```
sworddragon@ubuntu:~$ ls -a /proc/asound
.  ..  card0  cards  devices  hwdep  modules  pcm  SB  seq  timers  version
```

Has somebody an idea what is wrong here?


Edit: It seems this is a bug: [https://bugs.launchpad.net/ubuntu/+source/alsa-utils/+bug/1214633](https://bugs.launchpad.net/ubuntu/+source/alsa-utils/+bug/1214633)

---

### Post by monkey413 on 2013-10-04
you can see this page [http://askubuntu.com/questions/233060/recording-speaker-audio-using-avconv](http://askubuntu.com/questions/233060/recording-speaker-audio-using-avconv), it might be helpful.

---

