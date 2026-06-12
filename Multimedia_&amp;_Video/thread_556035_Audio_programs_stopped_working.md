---
title: "Audio programs stopped working"
date: 2007-09-20
forum: Multimedia &amp; Video
---

### Post by Heril on 2007-09-20
Earlier this week I got around to putting Ubuntu 7.04 on my Gateway laptop. The sound card works well and all, and for audio I prefer using mplayer from the command line, which was working fine for a while. However recently whenever I try to play my online playlist, or mp3s(I don have any other formats to check at the moment) Here is a copy of the output.
```
MPlayer 2:1.0~rc1-0ubuntu9.1 (C) 2000-2006 MPlayer Team
CPU: Genuine Intel(R) CPU           T1300  @ 1.66GHz (Family: 6, Model: 14, Stepping: 8)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.

Playing http://dialup.kawaii-radio.net:8000/.
Resolving dialup.kawaii-radio.net for AF_INET6...
Resolving dialup.kawaii-radio.net for AF_INET...
Connecting to server dialup.kawaii-radio.net[72.232.238.2]: 8000...
Name   : kawaii-radio dialup relay
Genre  : anime, japanese, game
Website: http://kawaii-radio.net
Public : yes
Bitrate: 24kbit/s
Cache size set to 320 KBytes

Cache fill:  0.00% (0 bytes)   
Cache fill:  0.00% (0 bytes)   
Cache fill:  0.00% (0 bytes)   
Cache fill:  0.00% (0 bytes)   
Cache fill:  2.50% (8192 bytes)   
Cache fill:  5.00% (16384 bytes)   
Cache fill: 10.00% (32768 bytes)   
Cache fill: 15.00% (49152 bytes)   
AAC file format detected.
==========================================================================
Forced audio codec: mad
Opening audio decoder: [faad] AAC (MPEG2/4 Advanced Audio Coding)
AUDIO: 32000 Hz, 2 ch, s16le, 128.0 kbit/12.50% (ratio: 16000->128000)
Selected audio codec: [faad] afm: faad (FAAD AAC (MPEG-2/MPEG-4 Audio) decoder)
==========================================================================

ICY Info: StreamTitle='‘ŠìŽµ£ (Aikawa Nanase) - natsu no hi no coral (7 seven)';StreamUrl='http://kawaii-radio.net';
```
And it just stops there. The results are similar for non-streaming files.

I also tried to play files off of each of my graphical media players and it worked for none of them.

I don't know if its a factor, but I use Beryl.

---

### Post by AstarothCY on 2007-09-21
There doesn't actually seem to be anything wrong in the output.
1. Does sound work otherwise? i.e. system sounds etc. If not, does sound work if you boot into a different OS?
2. Have you checked the volume controls in alsamixer?
3. Did this start happening after you installed or updated something?
4. Please try [this thread](http://ubuntuforums.org/showthread.php?t=205449).

---

