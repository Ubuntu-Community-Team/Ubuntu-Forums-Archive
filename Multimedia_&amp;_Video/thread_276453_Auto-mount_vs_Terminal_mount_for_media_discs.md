---
title: "Auto-mount vs Terminal mount for media discs"
date: 2006-10-12
forum: Multimedia &amp; Video
---

### Post by Eladon on 2006-10-12
Can someone explain to me or refer me to some docs regarding the difference between the auto-mount system built into Ubuntu vs the terminal mount command?

I would like to understand the process that Ubuntu (Gnome? or Nautilus?  Not sure exactly what software handles this) goes through to auto-mount multimedia discs (DVD Movies, Music CD's, etc).  I particularly want to learn what is unique about a mounted DVD, CD etc vs any other mounted volume.  For example, when you put a Movie DVD into your drive, Totem sees it as a disc and enables its "Play disc..." option.  But if I mount the same files to the same location (i.e. /media/cdrom0) via terminal (even if I mount an ISO into that path), the files are there, but the software doesn't see a "disc".

---

### Post by kidders on 2006-10-13
Hi there,

> **Eladon said:**
> But if I mount the same files to the same location (i.e. /media/cdrom0) via terminal (even if I mount an ISO into that path), the files are there, but the software doesn't see a "disc".

That's exactly right ... and, generally speaking, that's how people like it. When you mount something, it becomes just another part of your filesystem tree, so it's not really regarded as a device in its own right.

Basically, Linux has never liked this odd "drive" abstraction Microsoft seems so attached to. Over the years though, since there are just so many Windoze users around, people have tried to engineer something like it in the Linux world. Auto-mounted devices are handled using a _very_ complex network of little applications, and often screw up, for a variety of reasons.

In essence, all you ever have with Linux is a root filesystem with other filesystems plugged into it. The architecture is specifically designed to "hide" the fact that some of them may be networked, plugged into a USB port, on an optical disc, etc. Fairly obviously, the way to get best performance (in terms of application-level compatibility) is not to try to make it behave like Windows.

So, that's basically the difference. What you're referring to as auto-mounted things are an attempt to try to make Linux behave like Windows. When you mount something on your own, you effectively bypass the mechanisms that handle auto-mount operations, leaving you with what Linux is *really* doing underneath, rather than what it appears to be doing on the surface.

I hope that's of some help :-)

---

### Post by Eladon on 2006-10-13
Yes, it definately seems as though it's all about Linux trying to pretend it's Winblows.  Only catch is, SO much of the software is doing it.  I mentioned about Totem, but for example, I can't even figure out how to play a DVD in MPlayer with a disc mounted via terminal. When I try, it just says "Failed to open dvd://1" (whatever that means in Linux). 

So sadly, in order to educate myself to solve the problems that I'm having, I need to learn this lametastic crossover system that's been put in place.

I am having a problem related to all this, the post for my problem is here:
[http://www.ubuntuforums.org/showthread.php?t=274541](http://www.ubuntuforums.org/showthread.php?t=274541)

But I'm happy to solve my own problems, if someone can just point me in the right direction to learn about Ubuntu's disc mounting system.

---

### Post by kidders on 2006-10-13
Hey again,

I'm not sure about your other problem, but you should be able to get mplayer to play DVDs for you by asking it to play "dnav://" or "dvd://". This will only work though, if /dev/dvd exists. If it doesn't, let me know :-)

---

