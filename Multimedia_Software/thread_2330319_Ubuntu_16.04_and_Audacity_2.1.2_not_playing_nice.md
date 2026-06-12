---
title: "Ubuntu 16.04 and Audacity 2.1.2 not playing nice"
date: 2016-07-10
forum: Multimedia Software
---

### Post by Autodave on 2016-07-10
This isn't so much a question as it is an observation. Didn't really know where to post it.

I had been using Xubunu 14.04 and Audacity 2.0.5. I could record 18 channels from an Allen & Heath QU32 board. This was done via USB cable from board to computer. It worked. I did have to slightly reduce some parameters in Audacity, but it worked.

Upgraded to Xubunti 16.04 and that brought with it Audacity 2.1.2. Which did not work even with reduced parameters. What I got was a high pitched buzzing noise on every channel. The noise faded in, got loud enough to cover up whatever was on each channel, and then faded back out. This would take about 15 seconds to happen. Then about 2 minutes later, it would repeat. And, it kept doing this: 15 seconds noise, in 2 minutes repeat.

I tried Xubuntu 32 and 64 bit. I tried Ubuntu Studio 32 and 64 bit. I posted questions many places (including the Audacity forum), I read everything that I could read and tried every suggestion made. Nothing helped a bit, and most things made it worse: all the way to unusable at all. 

I even tried another, better machine. More speed, more memory, extra HD to record on. Nothing. Shut off all updating, screen blanker, all unnecessary background programs. Nothing.

Finally, went back to Xubuntu 14.04 32 bit and Audacity 2.0.5.  Everything worked just fine like it once had worked.

I don't know who, if anyone, needs to see this, but for what's it worth its here.

---

### Post by ajgreeny on 2016-07-10
Very odd, but not specifically due to the audacity version 2.1.2, which I already use successfully on my 14.04 Xubuntu system from the [https://launchpad.net/~ubuntuhandbook1/+archive/ubuntu/audacity](https://launchpad.net/~ubuntuhandbook1/+archive/ubuntu/audacity) ppa.

That ppa does not appear to have a xenial build, nor should one be necessary, as you already have the 2.1.2 version in 16.04, but I wonder if it is possible to test the any differences in builds by adding that ppa and installing audacity from that.

You could always try the daily builds of audacity from the ppa at [https://launchpad.net/~audacity-team/+archive/ubuntu/daily](https://launchpad.net/~audacity-team/+archive/ubuntu/daily) which does have a xenial version available.

If neither of those work for you, just remove the ppa, and then uninstall and reinstall audacity to get back to the standard repos version, or use ppa-purge package to do the same job.

Moved to **Multimedia Software** forum for a better fit.

---

### Post by Autodave on 2016-07-10
I fought with this for over a month: must have redone the 2 computers I was using about 6 times each. It is working now, and I believe it will stay that way forever. :-)

---

### Post by ajgreeny on 2016-07-11
> **Autodave said:**
> I fought with this for over a month: must have redone the 2 computers I was using about 6 times each. It is working now, and I believe it will stay that way forever. :-)
Do you know why?  What did you do?

---

### Post by Autodave on 2016-07-11
Like I posted above: tried both 32 and 64 bit versions. Tried changing buffer size and recording quality. The very best I got was the 15 seconds of buzzing noise every 2 minutes. I had changed every parameter, I added a second HD to record to: one HD for running the program, one for recording. The recording HD was a 7,200RPM with good sized cache. Tried better machine: 3.2 dual core (3 gig cache) with 8 gig RAM. Nothing usable at all. Went back to Linux 14.04 and Audacity 2.0.5. Upped the recording frequency, went to 32 bit float, 18 channels via USB cable and I have a great recording.

---

### Post by ajgreeny on 2016-07-11
Interesting, but I have no idea why you can not get Audacity to work on 16.04.

I have 16.04 only as a VM on a 14.04 host at the moment, but I'm just about to put Lubuntu 16.04 on a dual core Intel machine with 2GB ram and Intel integrated video; I will install audacity on that as soon as possible to see what happens and I'll then report back here.

Watch this space for more info.

---

### Post by Autodave on 2016-07-11
Understand: I could record 2 channel stereo via the stereo outputs on the board: that worked fine. The problem was using the USB and doing 18 channels.

---

### Post by ajgreeny on 2016-07-12
Ah! I missed that and have no experience of using USB sound hardware of any form, so don't think I can help you more with this.

Best of luck anyway; I hope you get this sorted before 14.04 loses support forcing you to move to some other version.

---

### Post by Autodave on 2016-07-12
Doesn't matter if 14.04 loses support: what I have now works and I won't ever change it until the machine dies. :-) I have updating shut off and the machine is not hooked to the internet, so I really don't have to worry about it. The way it is now can be the way it is 20 years from now.

---

