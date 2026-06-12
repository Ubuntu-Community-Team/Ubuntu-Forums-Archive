---
title: "is it time?"
date: 2006-08-24
forum: Multimedia &amp; Video
---

### Post by falkenberg_cph on 2006-08-24
Hi
So, i tried dapper and ubuntu-studio in the winter/spring, but was dissatisfied with the real-time recording. Therefore i went back to xp.

Now the questions is: is it time for us lost souls to return to linux. Has real-time become easier to configure while i was gone?

/Carsten

---

### Post by falkenberg_cph on 2006-08-24
Whoops.
Hadnt seen this thread:

[http://www.ubuntuforums.org/showthread.php?t=242807](http://www.ubuntuforums.org/showthread.php?t=242807)

Guess i stay in bills realm for a while ](*,) 

But its good news

/Carsten

---

### Post by dolson on 2006-08-25
You are using ambiguous terms.

The "realtime" patches that are being integrated into the kernel provide near-complete preemption, which means less Xruns during playback and recording at lower latencies. For many people, the default kernel is sufficient, but it really depends on many factors.

The ability for applications to request access to the "realtime" scheduler (SCHED_FIFO) has been in the kernel already, since 2.6.12. The method to allow access to SCHED_FIFO has been in several incarnations: realtime-lsm (now deprecated), running as root (bad idea), set_rlimits (good idea, if you are on Slackware or some other distro without PAM), or a sufficiently modern (or patched) PAM. Dapper ships both with an appropriate PAM and a kernel newer than 2.6.12, so there is no work for you to do on this front, aside from adding a couple entries to the /etc/security/limits.conf file.

There are also other things that can be modified such as IRQ priorities, something I have yet to dive into and document.

Really, aside from the kernel compile (which is optional and some people seem to be fine without), it's not hard to do this stuff.

Actually using the software is where my trouble comes in. The near total lack of updated (or any) documentation means you're on your own... That's what I want the wiki to solve, but so far, I've only got one tutorial and it's just to show the very basics of how to route in JACK. More will come as I have time to learn and document, or other people do the same. But I think that usability is more of an issue than configuring the system. Maybe I'm wrong.

---

### Post by zettberlin on 2006-08-25
Maybe you should have a look at this thread also:

[http://www.ubuntuforums.org/showthread.php?t=199803](http://www.ubuntuforums.org/showthread.php?t=199803)

I can do anything i usually do with soundapps on dapper-standard with latencies about 5-6 ms and i can go lower than 1 millisecond with some caution for things like playing only one Synth with a simple patch and 4-5 voices polyphony.

Jack runs all day, takes all the officejobs, Gimp, Mozilla etc plus playing songs with alsaplayer and having a little fun with muse and Zynadd and in the end there are about 20-25 xruns (within 12 h...). No crashes, no clicks and crackles etc. Of course it is not cool to have an xrun in the middle of a critical recording, yet in the middle of a critical recording i do not start Zynadd or Open office ;-)
Building your own patched kernel can sure improve that and add lots of headroom to that, still i stuck with the stockkernel and do alright.

---

### Post by dolson on 2006-08-26
And zett, someone (forget who, too lazy to look) posted a link stating that the "realtime" patches from ingo are going to be integrated hopefully by kernel 2.6.22, so the standard kernel won't even be an issue in due time. :D

That's the link above I think. Again, too lazy to look.

---

### Post by zettberlin on 2006-08-26
I found this one:

[http://www.serverwatch.com/news/article.php/3628036](http://www.serverwatch.com/news/article.php/3628036)

Long expected, hopefully here before long...

---

