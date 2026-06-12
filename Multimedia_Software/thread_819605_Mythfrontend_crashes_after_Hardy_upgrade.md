---
title: "Mythfrontend crashes after Hardy upgrade"
date: 2008-06-05
forum: Multimedia Software
---

### Post by Habbit on 2008-06-05
Hi there everyone. I'm quite puzzled by a mythtv problem that surfaced recently, just after updating to Hardy: mythfrontend works fine and smoothly, plays everything, etc. However, when I try to exit from "Live TV" or "Watch Recordings" the program dies with a segfault

Neither the back nor the frontend logs show anything special, and no file appears on /var/crash, but dmesg notices it:
```
[99577.520377] mythfrontend.re[11519]: segfault at b2449cc0 eip b2449cc0 esp bff1539c error 4
```
I believe the problem lies with the internal mythtv player, as the frontend does not crash when/after watching other videos (which use mplayer), just live TV or recordings. It is also strange that when watching TV recordings the crash doesn't happen when stopping the recording, but on exiting the menu.

I'd like to try and diagnose this: I'm armed with GDB and a lot of patience, and at least I want to pinpoint what module/dylib is causing the crash. However, my knowledge of GDB is poor at best - it's maybe my most-hated program after vi - so I'd like to receive information on what -dbg packages should I install, how to use GDB, etc. Or even better, if someone knew an outright solution to my problem... :popcorn:

---

### Post by Habbit on 2008-06-08
I'm impressed with this overload of feedback! Sorry for the sarcasm, but hey! are you alive, people? No matter, I just came back to tell I pinpointed the problem to the OpenGL libraries, in particular to a function called something like switchcontext or such...

The problem disappeared when I switched to the mythtv Qt rendered. Maybe it was an effect of using the open source radeon driver, even though my video card is theroretically fully supported (radeon 9600 pro). However, that does not completely explain the fact that it appeared only after upgrading to Hardy. Could something be wrong with my configuration? Is TVout stable in the open source driver?

---

### Post by oiper on 2008-08-21
I've never seen a thread with so much response! I hope someone reads this. 
I too was getting a similar error, but in reverse no less! Watching recordings/live tv was fine, exiting from a video (Internal,mplayer,xine,etc) caused the segfault. QT rendering was being used. 
The trick for me, thanks to this post pointing me in the right direction, was setting the QT style option just below the render option under Appearance. For whatever reason, this was blank. I set it to default and it works. 

I should note that I tried OpenGL and set it to default, which worked, then returned the renderer to QT. Perhaps changing to OpenGL and back fixed something. We may never know. :guitar:

```
Aug 21 07:50:28 mythbox kernel: [77084.680745] mythfrontend.re[9949]: segfault at 00000000 eip b226535f esp bfc5e240 error 6
```

---

### Post by asw20pilot on 2008-09-06
This is just to let you know that I have exactly the same problem as you. You describe it very well.

I am using ATI proprietary drivers, my distribution is Mythbuntu.

I will try to follow this thread in the hope that something comes up. If you need any further information from me (logs, tests, etc.) please let me know.

Mikkel

---

### Post by james113 on 2009-03-28
I'm having the exact same problem, but following an upgrade from Intrepid to Jaunty Beta.  Can anyone help?

---

### Post by Habbit on 2009-05-29
Have you tried the fixes suggested by all posters? What is your hardware and your rendering configuration? This thread is so old and mythtv has changed so much in the meantime that chances are that the problems are not related.

EDIT: big oops... sorry for re-resurrecting the thread. I read MAY 29th, not MARCH 29th :(

---

### Post by MountainX on 2009-11-07
I have the same or a similar problem with Mythbuntu 9.10 32bit, fresh install.

```
kernel: [  640.679757] mythfrontend.re[4486]: segfault at ffffffe8 ip 0116e88d sp bfafafb0 error 4 in libmythtv-0.22.so.0.22.0[c93000+a6c000]
```

I get this when starting "Watch TV"

I posted my logs here:
[http://www.mythtvtalk.com/forum/general/12203-mythtv-fails-4-4-computers-me-sagetv-ok.html#post48472](http://www.mythtvtalk.com/forum/general/12203-mythtv-fails-4-4-computers-me-sagetv-ok.html#post48472)

---

