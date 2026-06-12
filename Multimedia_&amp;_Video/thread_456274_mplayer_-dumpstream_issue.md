---
title: "mplayer -dumpstream issue"
date: 2007-05-27
forum: Multimedia &amp; Video
---

### Post by Rafael, Jr. on 2007-05-27
i'm having an issue with mplayer when trying to use the -dumpstream option.  It just hangs after this readout on my console:

mplayer -playlist rtsp://rm.z1.mii-streaming.net/media/pbs/quicktime_real/inthemix/SCHVIOCLIP2_PBS220.rm?v1st=EA4B5CF7B2DD10E3&altplay=SCHVIOCLIP2_PBS220.rm -dumpstream -dumpfile pbs.rm
[4] 3269
MPlayer 2:1.0~rc1-0ubuntu9 (C) 2000-2006 MPlayer Team
CPU: Intel(R) Pentium(R) 4 CPU 2.66GHz (Family: 15, Model: 2, Stepping: 9)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Resolving rm.z1.mii-streaming.net for AF_INET6...
bash: -dumpstream: command not found
violet@crills1:~$ Couldn't resolve name for AF_INET6: rm.z1.mii-streaming.net
Resolving rm.z1.mii-streaming.net for AF_INET...
Connecting to server rm.z1.mii-streaming.net[64.191.193.125]: 554...
Cache size set to 640 KBytes
Stream EOF detected
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Does anyone have any advice on how I can get this to work?

---

### Post by Rafael, Jr. on 2007-05-29
Solved my own problem.  When I copied and pasted the information from the link:

rtsp://rm.z1.mii-streaming.net/media/pbs/quicktime_real/inthemix/SCHVIOCLIP2_PBS220.rm[COLOR="Red"]?v1st=EA4B5CF7B2DD10E3&altpla y=SCHVIOCLIP2_PBS220.rm -dumpstream -dumpfile pbs.rm[/COLOR]

The text in red needed to be deleted and then the -dumpstream command was executed properly.

---

