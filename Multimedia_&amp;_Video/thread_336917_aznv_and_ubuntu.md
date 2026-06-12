---
title: "aznv and ubuntu"
date: 2007-01-12
forum: Multimedia &amp; Video
---

### Post by XVampireX on 2007-01-12
Hi, I'd like to ask if anyone could try to get this website streaming working under Ubuntu in any way: [www.aznv.tv/en](www.aznv.tv/en)

It's basically a service for streaming Asian movies/shows/etc... to people.

What I tried so far was to get it working with mplayer, which gave me that:

```

serge@serge-desktop:~$ mplayer -playlist Once_Upon_A_Time_In_High_School_-_Part_1.m3u
MPlayer 1.0rc1-4.1.2 (C) 2000-2006 MPlayer Team
CPU: Intel(R) Pentium(R) 4 CPU 1500MHz (Family: 15, Model: 0, Stepping: 7)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
98 audio & 216 video codecs
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing http://f4.aznv.tv/doStream/MTcyMTIsMDg4MDEwMWNiZGMyNzI0M2E0MTY1OThiOTNiMmNhMGY3ZGQ0YWM1YQ==/s.TYPE-bW92aWVz/s.ID-OA==/p.ID-MQ==/[TV]_Once_Upon_A_Time_In_High_School_-_Part_1.nsv.
Resolving f4.aznv.tv for AF_INET6...
Couldn't resolve name for AF_INET6: f4.aznv.tv
Resolving f4.aznv.tv for AF_INET...
Connecting to server f4.aznv.tv[38.119.52.194]: 80...
Resolving aznv.tv for AF_INET6...
Couldn't resolve name for AF_INET6: aznv.tv
Resolving aznv.tv for AF_INET...
Connecting to server aznv.tv[209.9.226.231]: 80...
Cache size set to 320 KBytes
Cache fill:  5.20% (17028 bytes)
Win32 LoadLibrary failed to load: avisynth.dll, /avisynth.dll, /usr/lib/win32/avisynth.dll, /usr/local/lib/win32/avisynth.dll
libavformat file format detected.
LAVF_header: av_open_input_stream() failed


Exiting... (End of file)
```

While when trying it with VLC gave me an error output in console, but it seemed to work, at least the audio. The error:

```

serge@serge-desktop:~$ vlc
VLC media player 0.8.6 Janus
[00000284] skins2 interface: skin: ASkin for VLC 0.8.6  author: Anton
[00000376] main decoder error: no suitable decoder module for fourcc `VP62'.
VLC probably does not support this sound or video format.

```

in xine(kaffeine) I can add it to my playlist but when I try to play it:

```

The connection was refused.
Check the host name. (invalid http answer)

```

```

04:39:49 PM: xine: cannot find input plugin for MRL [http://f4.aznv.tv/doStream/MTcyMTIsMDg4MDEwMWNiZGMyNzI0M2E0MTY1OThiOTNiMmNhMGY3ZGQ0YWM1YQ==/s.TYPE-bW92aWVz/s.ID-OA==/p.ID-MQ==/[TV]_Once_Upon_A_Time_In_High_School_-_Part_1.nsv]
04:39:49 PM: xine: input plugin cannot open MRL [http://f4.aznv.tv/doStream/MTcyMTIsMDg4MDEwMWNiZGMyNzI0M2E0MTY1OThiOTNiMmNhMGY3ZGQ0YWM1YQ==/s.TYPE-bW92aWVz/s.ID-OA==/p.ID-MQ==/[TV]_Once_Upon_A_Time_In_High_School_-_Part_1.nsv]
04:39:49 PM: input_http: invalid http answer
04:39:47 PM: xine: found input plugin  : http input plugin

```

This is what happens.

It looks like in their website, they listed mplayer as being able to play it, they also said that vlc just works, they didn't say xine though, but I figured, since xine can play alot of file formats as well, such as rmvb which just doesn't play in mplayer... Well it just doesn't work.

What's even funnier is that VP62 in VLC and mplayer works for people on Windows and some for macs too, and even as I looked in their forums, an ubuntu user also complained that it does not work.

mplayer 1.0rc1 has NATIVE support for VP62, and I'm using it via the package that 3v1n0 is providing, it may be that he didn't have something enabled during configure time but I doubt it since we're talking about native support.

and VLC out of all should have just worked (Although it did give me the best results out of all of them..), that's weird.

Please, help me.

Thanks.

---

### Post by XVampireX on 2007-01-23
Anyone?

---

