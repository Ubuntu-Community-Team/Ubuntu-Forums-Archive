---
title: "Problems using soundcard on server install"
date: 2011-01-15
forum: Multimedia Software
---

### Post by Twizzle on 2011-01-15
I have a 10.10 x64 fresh server install and am trying to use MPD to allow me to play my music through my stereo and control with MPoD on my iPhone.

I would appear to have set up MPD and MPoD correctly as I can see my database of music but when I try to play something it just shows the track on MPoD as paused and no sound comes out.

If I try to play the track through the server I get:
```
john@server:~$ mpc play
Moby - Great Escape
[paused]  #4/40   0:00/2:11 (0%)
volume: 60%   repeat: off   random: off   single: off   consume: off
ERROR: problems opening audio device
```

I thought I would check a few settings and got:

```
john@server:~$ aplay -l
aplay: device_list:235: no soundcards found...

```

and

```
john@server:~$ lspci | grep Audio
00:07.0 Audio device: nVidia Corporation MCP72XE/MCP72P/MCP78U/MCP78S High Definition Audio (rev a1)
01:06.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)

```

I am now reaching the limit of my Linux and Sound problems knowledge. To me it looks like it can see the Audio device but not the actual sound card part of it..

I know it has worked previoulsy as I used to have a 9.04 install with XBMC playing audio and video from the same system via an HDMI cable to my TV.

Any help would really be appreciated :D

---

