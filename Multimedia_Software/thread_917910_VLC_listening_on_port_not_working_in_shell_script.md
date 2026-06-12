---
title: "VLC listening on port not working in shell script?"
date: 2008-09-12
forum: Multimedia Software
---

### Post by frankvw on 2008-09-12
Head, meet wall. Wall, meet head.

I'm running VLC 0.8.6e (Janus) on Ubuntu 8.04.1 (Hardy) as follows:

```
    vlc --quiet --fullscreen --video-on-top --no-osd -intf rc --rc-host localhost:5555 --no-show-intf --verbose 0 --loop file://colorbars.wmv &

```

This works fine when I do it from the command line: VLC runs full screen and plays the specified WMV clip in an endless loop. I can telnet localhost at port 5555 and I get a console interface. However, when I include the above command line in a shell script, VLC does exactly the same, except that I get a "connection refused" when I try to telnet localhost at port 5555.

Question: does this issue originate with VLC or with Ubuntu? And how could I find out??

I've spent quite some time troubleshooting, and I'm stumped. What the ... is going on here? 

Please excuse me while I go bash my head against the wall some more. <thud> <thud> <thud> ... (*,)

// Frank

---

