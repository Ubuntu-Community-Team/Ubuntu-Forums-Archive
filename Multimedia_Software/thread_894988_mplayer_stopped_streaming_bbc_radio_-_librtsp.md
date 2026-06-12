---
title: "mplayer stopped streaming bbc radio - librtsp"
date: 2008-08-19
forum: Multimedia Software
---

### Post by spadger on 2008-08-19
It seems that mplayer is having problems streaming bbc radio and listen again content since approximately 12th August 2008 ( i have a daily script which stopped working after this date). Everything was working fine up to that point and then i'm not sure what happened (maybe an update?)

I've tried the same on two of my machines, both having a pretty similar setup and both giving the same problem. The stream can still be played from realplayer without any problems.

I'm not sure if its somehow linked to librtsp so I was hoping one of you clever people might be able to help.

Here's what's happening:

james@james-laptop:~/bin$ mplayer -playlist [http://www.bbc.co.uk/radio/aod/shows/rpms/6music/6m_adamjoe.rpm](http://www.bbc.co.uk/radio/aod/shows/rpms/6music/6m_adamjoe.rpm)
MPlayer 1.0rc2-4.2.3 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Pentium(R) M processor 1.73GHz (Family: 6, Model: 13, Stepping: 8)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Resolving [www.bbc.co.uk](www.bbc.co.uk) for AF_INET6...
Couldn't resolve name for AF_INET6: [www.bbc.co.uk](www.bbc.co.uk)
Resolving [www.bbc.co.uk](www.bbc.co.uk) for AF_INET...
Connecting to server [www.bbc.co.uk](www.bbc.co.uk)[212.58.251.195]: 80...
Cache size set to 320 KBytes
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing rtsp://rmv8.bbc.net.uk/6music/6m_adamjoe.ra?BBC-UID=9498dafb05a045dd036f257dd000483671b497931040a164c4cf19b792a6163b_n&SSO2-UID=.
Resolving rmv8.bbc.net.uk for AF_INET6...
Couldn't resolve name for AF_INET6: rmv8.bbc.net.uk
Resolving rmv8.bbc.net.uk for AF_INET...
Connecting to server rmv8.bbc.net.uk[212.58.224.141]: 554...
librtsp: server responds: '&#65533;OPTIONS * RTSP/1.0'
rtsp: read error.
librtsp: server responds: '&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;H,H,2'


MPlayer interrupted by signal 13 in module: open_stream
- MPlayer crashed. This shouldn't happen.
  It can be a bug in the MPlayer code _or_ in your drivers _or_ in your
  gcc version. If you think it's MPlayer's fault, please read
  DOCS/HTML/en/bugreports.html and follow the instructions there. We can't and
  won't help unless you provide this information when reporting a possible bug.

---

### Post by spadger on 2008-08-23
An update just for information. I tried running the script from work and everything worked fine so I'm guessing it might be a router "upgrade" or something coming from my ISP. I'm with orange in france with a Sagem livebox if that helps anyone else diagnose a similar problem.

Not sure if I can do much about it as I'm not so confident messing with router settings etc. we'll see. If anyone has any tips I'd be glad to hear them.

Cheers,

J.

---

