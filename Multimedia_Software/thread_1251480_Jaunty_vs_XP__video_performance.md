---
title: "Jaunty vs XP : video performance"
date: 2009-08-27
forum: Multimedia Software
---

### Post by ticket on 2009-08-27
Today I tried a little experiment to compare video playback performance between Jaunty 9.04 and Windows XP.  

The comparison wasn't totally fair, but I was surprised how badly Jaunty did.  A fair comparison should be done with a dual boot machine. What I had to hand, however, were two Dell machines, one a little old, the other older. Here are their specs:

Oldest PC, running Ubuntu 9.04:
- Intel P4 1.5GHz
- 512MB RAM
- GeForce 6200 PCI, 180.44 nVidia driver
- 1440x900 LCD monitor

Somewhat newer PC, running Windows XP SP3:
- AMD Sempron 3400+ 1.8GHz
- 512MB RAM
- GeForce 6150LE, HyperTransport, integrated
- 1024x768 LCD monitor

The machines are not wildly different in their specs. The Windows graphics card may have the edge on bus bandwith, but its fill rate is less than the 6200 on Jaunty:

fill rates:
GeForce 6150LE	425 MP/s
GeForce 6200	600 MP/s 

Also the 6200 has better 3D performance according to the specs, but we are only comparing 2D performance in this 'test'.

I used two video files:
    MP4(H.264)        25 fps  1280x720  
    WMV(v9 advanced)  24 fps  1920x816

On the Windows machine I used Windows media player to play the WMV file, and the latest quicktime player to play the MP4 file.

On the Jaunty machine I used the latest mplayer build (from svn). Compiz was switched off. No filters were used. mttr was set correctly.


On Jaunty, the MP4 file played smoothly, but its smoothness was simply because it was playing the video back in slow motion!  However, the audio was racing ahead, so the sound and video were totally out of sync. The same happened when playing in a window and in full screen mode.

On Windows, quicktime played the video flawlessly, no matter how I set the view, e.g. in full screen, fit to window, zoom of 1 (when it would not fit into the monitor screen).


Next I tried the wmv.  I fully expected the Windows machine to choke, but no - it played back almost flawlessly! There was a slight, very occasional stutter now and then, nevertheless the video was most certainly watchable and enjoyable.

On Jaunty, the wmv was again in slow motion, but this time the video was also stuttering. The sound sputtered and eventually gave up. I tried using OSS for the sound driver instead of pulse - slight improvement in sound for the first few seconds, then stuttering badly. Basically, it was unwatchable.

Just to rub salt in the wounds, the Windows machine could play normal resolution youtube videos in full screen with no problem at all. In Jaunty, full screen flash became a slide show, which was troublesome to stop (hit escape key and wait, wait ...)

My experiment was really (to some extent) testing the differences between the OS's and the graphics drivers (no firefox and flash in the loop).  It seems to indicate that there is a problem with the nVidia / xorg drivers on Jaunty or Linux in general. 

As I said, it is not a totally fair comparison, but I was amazed all the same. Perhaps someone can do the same tests using a dual boot system?

---

### Post by inobe on 2009-08-27
disable desktop affects in ubuntu then make the comparison !

or even better' add desktop affects in xp ......

though you will need a 9800gtx to run the affects smoothly.

---

### Post by ticket on 2009-08-27
> **inobe said:**
> disable desktop affects in ubuntu then make the comparison !

or even better' add desktop affects in xp ......

though you will need a 9800gtx to run the affects smoothly.

Compiz was off. Ubuntu visual effects were set to 'None' in the tests ...

---

### Post by HappyFeet on 2009-08-27
I am a mutimedia junkie and videos/music are of most importance to me. I have had no issues with anything. If I did, I would not be using ubuntu. 

Your comparison is definitely not scientific by any means. I suggest finding a better computer and dual booting.
> **ticket said:**
>  Perhaps someone can do the same tests using a dual boot system?
Does installing ubuntu on over 40 computers without issue count? (and yes, I tested all sorts of videos, flash and music on all of them)

You may have hardware issues without realizing it.

---

### Post by ticket on 2009-08-27
> **HappyFeet said:**
> I am a mutimedia junkie and videos/music are of most importance to me. I have had no issues with anything. If I did, I would not be using ubuntu. 

Your comparison is definitely not scientific by any means. I suggest finding a better computer and dual booting.

Does installing ubuntu on over 40 computers without issue count? (and yes, I tested all sorts of videos, flash and music on all of them)

You may have hardware issues without realizing it.

You may be right, but a quick search of the forums (and other Linux forums) shows mine is not an isolated case by any means - it is a very common problem. When it comes to full screen, 720 flash, it can even bring powerful machines to their knees. But flash is closed source, so no point arguing that one.

I thought one of the benefits of Linux is that it breathes new life into old machines. If I thought I had to buy a powerful machine to just get decent video going on Linux, then I might as well stick with my old machine and use windoze instead. 

I'd be interested in knowing what PC and graphics card combination you recommend, and what a min spec machine is these days for Linux video watching.  Heck, I could get my really really old 400MHz PIII play DVDs in software using VLC in XP. But not with Ubuntu.

Don't get me wrong - I am fully committed to Ubuntu (that's why I don't dual boot - the other windoze machine is not mine). But I don't think the best performance is being squeezed out of older machines by present software.

---

### Post by ticket on 2009-08-28
Well, it looks like happyfeet could be right.

I used a knoppix live cd to boot the windoze machine. Thanks to the knoppix guys, their live cd has a recent mplayer that can play wmv and mp4 files.  When I played the test files, there were no problems at all. Some things to note, however, were that the monitor resolution was stuck at 800x600 and there was no sound. No amount of fiddling could fix that.  Also compiz couldn't be enabled for some reason, so I guess I wasn't using an nvidia driver. I wasn't able to install a flash player, so I couldn't test that aspect.  So apart form the untested flash, both windows XP and and Linux have the same (good) performance on the Sempron/6150LE machine.

When trying knoppix on my Intel/6200 PC, I got the same problems with the test videos as before (slow motion & stuttering).

If the knoppix CD is not using nvidia drivers, then this means nvidia drivers are not the cause of my problems on the older 6200 machine.  And neither is the Linux architecture, it seems.

The problem simply points to the hardware on the older machine.  Now both machines have CPUs that aren't too different in performance,

[Edit : Not true. The Sempron has performance on par with a P4 3GHz. This surprised me as the Sempron machine was bought as the lowest / cheapest Dell machine available a few years ago] 

so the problem appears to lie in the 6200 graphics card and its interface, or that the 6150LE is somehow much better than the 6200. Maybe the limited bandwidth of a PCI card is the problem.  The Intel PC does have a spare slot for an AGP x4 card, but these type of cards seem rare these days.  It would be a shame to dump the Intel 1.5GHz machine for the sake of better video performance, but that may be the only other option left.

[Edit : Advice from the NV forums suggests getting an nVidia 8400 GS.  This will decode all HD streams.  But may need to upgrade the 250W PSU to 400W. Will be interesting to see if a 8400 GS helps flash video performance in any way, and whether the PCI interface is a significant bottleneck].

---

