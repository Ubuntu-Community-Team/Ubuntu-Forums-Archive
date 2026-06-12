---
title: "How to record an .m3u stream?"
date: 2008-11-17
forum: Multimedia Software
---

### Post by tmcarson1 on 2008-11-17
I recorded an .m3u radio show once before, and now I cannot remember how I did it.

I tried streamripper but it just gets stuck at connecting.

Any thoughts on a program to record a 1 hour radio program that is streaming in the .m3u format?

Thanks much for any help!

---

### Post by andrew.46 on 2008-12-25
Hi,

I can give an example using the svn MPlayer:

```
$ mplayer -cache 1024 \
http://www.radio1001.org/people/yomguy/radio1001.m3u/at_download/file \
-vc null -vo null -ao pcm:fast:waveheader:file=download.wav
```

and then convert the downloaded wave file to the format of your choice. This is the process in motion:

```
andrew@skamandros:~/Desktop$ mplayer -cache 1024 \
> http://www.radio1001.org/people/yomguy/radio1001.m3u/at_download/file \
> -vc null -vo null -ao pcm:fast:waveheader:file=download.wav
MPlayer dev-SVN-r28174-4.3.2 (C) 2000-2008 MPlayer Team
CPU: Intel(R) Core(TM)2 CPU         T5500  @ 1.66GHz (Family: 6, Model: 15, Stepping: 2)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled for x86 CPU with extensions: MMX MMX2 SSE SSE2

Playing http://www.radio1001.org/people/yomguy/radio1001.m3u/at_download/file.
Resolving www.radio1001.org for AF_INET6...
Couldn't resolve name for AF_INET6: www.radio1001.org
Resolving www.radio1001.org for AF_INET...
Connecting to server www.radio1001.org[91.121.8.116]: 80...
Cache size set to 1024 KBytes


Playing http://stream.parisson.com:8000/radio1001_1.mp3.
Resolving stream.parisson.com for AF_INET6...
Couldn't resolve name for AF_INET6: stream.parisson.com
Resolving stream.parisson.com for AF_INET...
Connecting to server stream.parisson.com[91.121.8.116]: 8000...
Name   : Radio1001
Genre  : Various
Website: http://radio1001.org
Public : yes
Bitrate: 192kbit/s
Cache size set to 1024 KBytes
Cache fill:  0.78% (8192 bytes)   
ICY Info: StreamTitle='Stendec, Live@Project-101';
Cache fill: 19.53% (204800 bytes)   
Audio only file format detected.
==========================================================================
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
mpg123: Can't rewind stream by 116 bits!
AUDIO: 44100 Hz, 2 ch, s16le, 160.0 kbit/11.34% (ratio: 20000->176400)
Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)
==========================================================================
[AO PCM] File: download.wav (WAVE)
PCM: Samplerate: 44100Hz Channels: Stereo Format s16le
[AO PCM] Info: Faster dumping is achieved with -vc null -vo null -ao pcm:fast
[AO PCM] Info: To write WAVE files use -ao pcm:waveheader (default).
AO: [pcm] 44100Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...
A:  17.5 (17.4) of -0.0 (unknown) 32.7% 0% 
```

Hope this helps?

 Andrew

---

### Post by tmcarson1 on 2009-07-10
Thanks I will give that a try.

---

### Post by andrew.46 on 2009-07-10
Hi tmcarson,

> **tmcarson1 said:**
> Thanks I will give that a try.

Mind you I guess if it is definitely an mp3 stream another technique would be probably be a *better* idea, and this is the benefit of looking at older posts with a bit more experience :-).

I illustrate this technique with a real mp3 stream so you can perhaps experiment a little:

```

mplayer -cache 1024 \
        -playlist http://www.abc.net.au/streaming/classic/classicfm.m3u \
        -dumpstream -dumpfile abc_classic_FM.mp3

```

This is all a single command so just copy and paste it into a terminal, perhaps running:

```
cd $HOME/Desktop
```

first so the resulting file is not lost :-).

All the best,

Andrew

---

