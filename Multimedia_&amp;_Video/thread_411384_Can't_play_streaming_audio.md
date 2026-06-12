---
title: "Can't play streaming audio"
date: 2007-04-16
forum: Multimedia &amp; Video
---

### Post by wormser on 2007-04-16
I am trying to listen to [RushRadio.org]("http://www.rushradio.org") with Mplayer.  I followed [this guide]("http://onlyubuntu.blogspot.com/2007/03/install-mplayer-and-multimedia-codecs.html") to install Mplayer with the libdvdcss2 and w32 codecs.  The player gets to 60% buffering and stops.  

I was able to get it to play in xmms so the codec should not be the problem.  Any ideas how to get it working in Mplayer?

Thanks

---

### Post by guysmiley25 on 2007-05-11
Ok when I went there, my mozilla-mplayer would not play it. It got stuck buffering. And would then stop.

So I tryed from the terminal:
```
mplayer http://205.188.215.229:8010
```

And this was the output:
```

MPlayer 2:1.0~rc1-0ubuntu9 (C) 2000-2006 MPlayer Team
CPU: Intel(R) Pentium(R) 4 CPU 3.06GHz (Family: 15, Model: 2, Stepping: 9)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing http://205.188.215.229:8010.
Resolving 205.188.215.229 for AF_INET6...
Couldn't resolve name for AF_INET6: 205.188.215.229
Connecting to server 205.188.215.229[205.188.215.229]: 8010...
Authentication required.
Authentication failed. Please use the -user and -passwd options to provide your
username/password for a list of URLs, or form an URL like:
http://username:password@hostname/file
STREAM_ASF, URL: http://205.188.215.229:8010
Resolving 205.188.215.229 for AF_INET6...
Couldn't resolve name for AF_INET6: 205.188.215.229
Connecting to server 205.188.215.229[205.188.215.229]: 8010...
unknown ASF streaming type
Failed, exiting.
Resolving 205.188.215.229 for AF_INET6...
Couldn't resolve name for AF_INET6: 205.188.215.229
Connecting to server 205.188.215.229[205.188.215.229]: 8010...
Authentication required.
Authentication failed. Please use the -user and -passwd options to provide your
username/password for a list of URLs, or form an URL like:
http://username:password@hostname/file
File not found: '205.188.215.229:8010'
Failed to open http://205.188.215.229:8010.


Exiting... (End of file)

```

So I think you need to try:
```

mplayer http://205.188.215.229:8010 -user wormser -passwd xxxx

```

Hope that helps you out.

---

### Post by wormser on 2007-05-16
Thanks.  It does work threw the command line with just mplayer [http://205.188.215.229:8010](http://205.188.215.229:8010).

---

