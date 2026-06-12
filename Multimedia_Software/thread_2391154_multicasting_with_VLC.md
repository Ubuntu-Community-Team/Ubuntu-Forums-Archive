---
title: "multicasting with VLC"
date: 2018-05-06
forum: Multimedia Software
---

### Post by cpdondo on 2018-05-06
I have a file I need to multicast to an audience next week.

The source file plays well with VLC; it was encoded with handbrake using my standard H.264 settings.

```

vlc -vvv source.m4v --sout '#rtp{access=udp,mux=ts,dst=224.255.1.1,port=5004,sap,group="Video",name=Jumper Movie"}' :sout-all

```

I have tried variants of the above; everything produces the same result.

The streaming part works fine; I can see packets flowing with tcpdump (on the streaming laptop):

```

11:52:19.669762 IP yan-ThinkPad-W530.55408 > 224.255.1.1.5004: UDP, length 1328
11:52:19.669782 IP yan-ThinkPad-W530.55408 > 224.255.1.1.5004: UDP, length 1328
11:52:19.669798 IP yan-ThinkPad-W530.55408 > 224.255.1.1.5004: UDP, length 1328
11:52:19.672014 IP yan-ThinkPad-W530.55408 > 224.255.1.1.5004: UDP, length 1328
11:52:19.674146 IP yan-ThinkPad-W530.55408 > 224.255.1.1.5004: UDP, length 1328
11:52:19.674158 IP yan-ThinkPad-W530.55408 > 224.255.1.1.5004: UDP, length 1328
11:52:19.674167 IP yan-ThinkPad-W530.55408 > 224.255.1.1.5004: UDP, length 1328
11:52:19.677002 IP yan-ThinkPad-W530.55408 > 224.255.1.1.5004: UDP, length 1328

```

However, no client can view the stream.  They connect but only show black.

On a linux client I get the following errors:

```

[00007f83cc000ba8] ts demux error: libdvbpsi error (PSI decoder): TS discontinuity (received 7, expected 0) for PID 0
[00007f83cc000ba8] ts demux error: libdvbpsi error (PSI decoder): TS discontinuity (received 7, expected 0) for PID 66
[00007f83cc000ba8] ts demux error: libdvbpsi error (PSI decoder): TS discontinuity (received 10, expected 2) for PID 0
[00007f83cc000ba8] ts demux error: libdvbpsi error (PSI decoder): TS discontinuity (received 10, expected 1) for PID 66
[00007f83cc000ba8] ts demux error: libdvbpsi error (PSI decoder): TS discontinuity (received 15, expected 13) for PID 66
[00007f83cc000ba8] ts demux error: libdvbpsi error (PSI decoder): TS discontinuity (received 0, expected 14) for PID 0
[00007f83cc000ba8] ts demux error: libdvbpsi error (PSI decoder): TS discontinuity (received 1, expected 10) for PID 66
[00007f83cc000ba8] ts demux error: libdvbpsi error (PSI decoder): TS discontinuity (received 2, expected 10) for PID 0
[00007f83cc000ba8] ts demux error: libdvbpsi error (PSI decoder): TS discontinuity (received 15, expected 12) for PID 66
[00007f83cc000ba8] ts demux error: libdvbpsi error (PSI decoder): TS discontinuity (received 0, expected 12) for PID 0

```

From everything I've read, it should "just work".  It doesn't for me.

I have tried this with VPC on an iPad, android phone, and a linux laptop; none of them will play.

Anyone have any ideas?

---

