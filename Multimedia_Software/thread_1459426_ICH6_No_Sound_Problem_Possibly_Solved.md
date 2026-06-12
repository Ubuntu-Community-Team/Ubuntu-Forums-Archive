---
title: "ICH6 No Sound Problem Possibly Solved"
date: 2010-04-21
forum: Multimedia Software
---

### Post by SRST Technologies on 2010-04-21
Are you having problems with ICH6 sound, especially if it worked before and is no longer working when you didn't do anything drastic?  Do you only get sound out of the headphones?

We're investigating why.  That's the soundcard two of our workstations use.  When we upgraded to the latest kernel available we thought it killed the entire module for sound completely.  Turns out that is not the case.

Reading on the boards, we discover many of you have the same problem.  At this point we are extremely reluctant to say it's a kernel problem, but it will still produce the same result when you cat an uncompressed wav file to the sound card device too, so maybe it is.  We don't know yet.

In the mean time, here's the easy fix... move the 1/8" jack that is entering your sound device to another port on the sound device while trying to play music (if you can).  Yes, we know that you're only supposed to get sound out of the speaker out port.  Try it anyways.  If you don't succeed on the first try, try the rest of your ports sequentially.  Eventually you'll hear sound again.

However, every reboot is going to force you to do this procedure over and over until we can figure out what is going on and how to submit our fix.

The Bug List is being notified.  Happy hacking.

---

