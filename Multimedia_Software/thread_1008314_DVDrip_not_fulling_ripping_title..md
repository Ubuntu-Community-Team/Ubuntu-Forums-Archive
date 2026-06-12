---
title: "DVD::rip not fulling ripping title."
date: 2008-12-11
forum: Multimedia Software
---

### Post by needmorecowbell on 2008-12-11
I'm new to the forums, so pardon me if I'm posting incorectly. Also, I tried searching, but did not see this issue come up.
I'm running ubuntu 8.04 (hardy) and using DVD::rip. The problem I'm having is that it's not ripping the DVD correctly. I've uploaded the two screenshots to better explain. Firstly, the status bar at the bottom of the ripping screen never goes to fully completed when it gets to title #4. It stops at 70%. Then when you look at the details, it has jobs that are waiting, but when you look at the log it says the title finished.

Here's the bottom section of the log file:

Thu Dec 11 09:34:29 2008 Rip - title #4: 10% done.
Thu Dec 11 09:35:56 2008 Rip - title #4: 20% done.
Thu Dec 11 09:36:56 2008 Rip - title #4: 30% done.
Thu Dec 11 09:38:01 2008 Rip - title #4: 40% done.
Thu Dec 11 09:39:16 2008 Rip - title #4: 50% done.
Thu Dec 11 09:41:04 2008 Rip - title #4: 60% done.
Thu Dec 11 09:42:56 2008 Rip - title #4: 70% done.
Thu Dec 11 09:43:35 2008 Executing command: execflow tcprobe -H 25 -i /home/user/jdata/dvdrip-data/apocal/vob/004/ && echo EXECFLOW_OK
Thu Dec 11 09:43:37 2008 DVD TOC reported wrong framerate 29.97, adjusted frame rate to 23.976 and frame count to 187268
Thu Dec 11 09:43:38 2008 Program stream units calculated
Thu Dec 11 09:43:38 2008 Enabled PSU core. Movie is NTSC and has more than one PSU.
Thu Dec 11 09:43:38 2008 Job 'Process title #4' finished
Thu Dec 11 09:43:38 2008 Job 'Rip - title #4' finished

Now, I have successfully ripped several of my own encrypted DVDs, but a couple have done this to me, I'm thinking it's a problem with the disc, but I'm not sure. I see it adjusted an incorrect framerate, but didn't know if this was a contributing factor.

Any help would be appreciated.

Thanks,

--needmorecowbell

---

### Post by wolfen69 on 2008-12-11
you could also try xdvdshrink, k9copy, or devede.

---

### Post by howefield on 2008-12-11
Can't help you with the actual problem other than suggest yet another program, called handbrake, first class and fast especially if you have a multi core processor. Unfortunately not in the repos., but available at handbrake.fr

Also as wolfen69 suggests, Devede is excellent.

---

### Post by needmorecowbell on 2008-12-11
I might look to those other programs at a later date, but really would like to this tackled for DVD::rip as it has worked really well so far.

---

### Post by forbjok on 2008-12-15
I seem to be having the same problem.

I've ripped several movies before, both region 1 and 2, without problems, but when I try to rip my region 1 NTSC copy of "The Stupids", this happens every time. (the progress just seems to freeze at 70-80%, and nothing more happens - no error message, and it seems impossible to cancel - the ripping process just freezes forever, and I have to close DVD::rip and restart it)
The DVD contains 2 video tracks, one 4:3 and another 16:9. Same thing happens when attempting to rip either.

I tried installing Medibuntu, but it seems to have made no difference.

The other alternatives mentioned seem to be intended for re-encoding DVD9s to fit on a DVD5 rather than ripping/encoding to video files. (i haven't tried them, but that's what it looks like from the descriptions i found on them)

Can they be used to rip to files as well, or if not, are there any other good alternatives to DVD::rip for this type of ripping?

Better yet, is there some way to get DVD::rip to work correctly?

---

### Post by needmorecowbell on 2008-12-15
Glad I'm not the only one having this issue. I still have not been able to find a solution to this issue.

---

### Post by forbjok on 2008-12-15
Do you get the problem with all movies, or just some specific ones?

EDIT:
Just to add a few more bits of information...

I just watched the entire movie on the same computer, in the same DVD drive without any problems, so there is definitely nothing wrong with the DVD.

Also, I tried re-ripping a different movie which I ripped before (Heavenly Creatures, region 1 NTSC), to see if it could be anything on my system that had changed, and DVD::rip still manages to rip that fine.

So it must be a bug in DVD::rip or one of its dependencies combined with certain DVD titles that causes something to go wrong. I still don't see what the difference would be though, since both DVDs are region 1 NTSC, and anyway I've ripped PAL DVDs too.

---

### Post by needmorecowbell on 2008-12-15
It seems to be with specific ones. And yes, they play fine in the same DVD recorder, just a problem ripping them. Definitely is something with the program. My latest attempt was this morning with, Batman the Dark Knight, and it failed, just like a other one, at 70%. Weird. I don't think it's an encryption error, unless a new patch has come out. ?

---

### Post by aleko74 on 2008-12-24
Hi,

I'm having the same problem with two DVDs now. With one, ripping stops after 70%, with another - after 50%.

With other discs, DVD::rip works well.

---

### Post by clarkburbidge on 2009-01-03
I'm having the same exact problem. I just did 2 movies before this and now this one is halting at 70% also on Dark Night.

---

### Post by aleko74 on 2009-01-05
I believe the problem is due to some DVDs having errors and being unreadable. I have this problem with some discs scratched by my kids. It looks like dvd::rip just doesn't catch or report the read error and stops ripping silently.

I have ordered a new DVD drive, and it arrives tomorrow. I'll try these problematic discs to see if there is any difference.

---

### Post by xc3RnbFO8P on 2009-01-05
You can install **Dvdisaster** in Add/Remove (all available application)
and check DVDs for errors.

---

### Post by nadiutta on 2009-01-05
my problem is the same but even worst: the rip stop at 0.00% :(
It start for a few second and then it stop.
Also I can't see the preview of the frames...

p.s. I'm new with ubuntu...(8.04)

---

### Post by derekroyce on 2009-01-11
Same problem with DarkKnight, Wall-E, and Step Brothers: fail at about 70%.

Most older movies are okay.

---

### Post by aleko74 on 2009-01-14
I was able to rip a couple of discs with the new DVD drive I've just bought. However, I still have a few DVDs that have problems.

---

### Post by The_R on 2009-05-13
I was wondering if anyone found a way to fix this yet. I am having the same problem with a brand new, never been used DVD (Pirates of the Caribbean, At World's End). It gets to around 60% then just stops. No error message, no stop button to click, not even a "have a nice day, jerk." Just a happily idle page that won't respond to even the most furious of clicks.
I hate messing with DVDs. I like to store then on my computer and organize them with Gstar, but for some of them, I still have to have a big clunky DVD case sitting on the shelf. I'm seriously thinking about downloading it from the internet. I mean, I already paid for it, so it should be ok right?

---

