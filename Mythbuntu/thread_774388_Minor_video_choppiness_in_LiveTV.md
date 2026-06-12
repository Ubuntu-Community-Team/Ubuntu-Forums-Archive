---
title: "Minor video choppiness in LiveTV"
date: 2008-04-29
forum: Mythbuntu
---

### Post by smaug42 on 2008-04-29
I am having a minor problem with video choppiness in LiveTV.
My Mythbuntu install is running on 
 - Hauppauge Nova-T-Lite USB
 - 1GB RAM
 - AMD Semperon 64 LE 1100 (1900MHz)
 - 320GB SATA hard drive

Playback from the recorded (DVD-T) LiveTV is flawless, but when watching the live broadcast, there is an almost constant minor video jitter/micro-pausing.  Audio is clean.

I have done some digging on this, and some people have recommended turning on DMA... how can you do this on SATA drives?  Is it possible?  Is this really the cause of the problem?

I did a throughput/benchmark test (hdparm -tT) on the drive and got results over 75MB/sec.

Is there anything I can do to clear this up?

---

### Post by laga on 2008-04-29
This might be far-fetched, but do you have more than one audio stream? You can see that by pressing "m" during playback, then selecting the corresponding menu entry.

Since it only happens in LiveTV, it could also be the problem where the correct playback profile isn't applied: [http://svn.mythtv.org/trac/ticket/5025](http://svn.mythtv.org/trac/ticket/5025)

But that probably only applies if you're using HD.

---

### Post by smaug42 on 2008-04-30
Doing more digging on this.  I checked for extra audio themes and also checked the video profiles... I set the video profile to the lowest setting and no changes.. not worse, and not better.

I looked at CPU usage, and when I am watching LiveTV, CPU use pegs to 100% and stays there.  mythfrontend.re is the culprit.

The CPU this is running on should be way more than is needed to get smooth playback... and AMD Semperon64 LE-1100 (1.9GHZ) in this system:
[Asus P2 M2A690G]("http://www.asus.com/products.aspx?l1=1&l2=3&l3=483&l4=0&model=1797&modelmenu=2")
I'm running at 640x480 resolution, and using the ATI proprietary drivers... I set the shared vram to 256mb.. (since I did this as part of the trouble shooting, I do see (more?) swap partition activity)

During recorded video playback (mpg or avi) CPU use rarely hits even 10%...

The stuttering video though... it's making TV painful to watch.  It's better to set it to record, and watch the perfect recorded TV show.

I had the DVB-T tuner connected to my main computer running MythTV and it was DVD quality smooth... so I assume the tuner works OK.

Kinda of at a loss here as to where to go next :-(

---

### Post by smaug42 on 2008-04-30
I did find one setting that sometimes gives a significant improvement to the LiveTV... Press m, and then select Video Scan and set it to Progressive.  This has a noticeable and immediate impact on the video "watchability"  It is still not smooth like I would expect it to be (I expect the exact same quality from LiveTV as I get from the recorded playback).  CPU use is still pegged at 100% and stays there.

I also bumped resolution up to 800x600 (from 640x480) and that has no noticeable negative impact on the playback.

I wonder... would it make a difference if I switched to the 32 bit version (instead of using the 64bit Mythbuntu)??

---

