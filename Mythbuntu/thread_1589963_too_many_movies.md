---
title: "too many movies"
date: 2010-10-07
forum: Mythbuntu
---

### Post by blkbx on 2010-10-07
Hi
I've just finished my mythbuntu 10.4 install and have loaded my room mates movies and audio as well as my own. That left very little space on the drive 46G. Now the box locks up won't boot on restart and well just sits there. I'm wondering if adding so much media may have caused this. Although I have been able to use mythtv just after I loaded everything.
My backend sys which is the one that locks up is a home built pc from a couple of years ago.
it has a msi k8n neo board, not the platinum version. One gig of geil  pc 3200 ddr 400 cl =2-6-3-3. Two X1t hhd. Is the system ok or am I asking too much of it.
thanks in advance.
ps just to clarify. it locks up completely, nothing going to the monitor, num lock on the keyboard doesn't come on when pressed.

---

### Post by BbUiDgZ on 2010-10-07
> **blkbx said:**
> Hi
I've just finished my mythbuntu 10.4 install and have loaded my room mates movies and audio as well as my own. That left very little space on the drive 46G. Now the box locks up won't boot on restart and well just sits there. I'm wondering if adding so much media may have caused this. Although I have been able to use mythtv just after I loaded everything.
My backend sys which is the one that locks up is a home built pc from a couple of years ago.
it has a msi k8n neo board, not the platinum version. One gig of geil  pc 3200 ddr 400 cl =2-6-3-3. Two X1t hhd. Is the system ok or am I asking too much of it.
thanks in advance.
ps just to clarify. it locks up completely, nothing going to the monitor, num lock on the keyboard doesn't come on when pressed.

whats your logs say?
tbh it sounds like a hardware error to me but its very hard to be sure without any logs.
EDIT: hows the temp?

Run memtest86

---

### Post by klc5555 on 2010-10-07
Of course, if you can't boot and can't get through or even to the power-on hardware self-check, the log and memtest86 thing is going to be a bit difficult.

Do the fans spin (and LEDs light)? If not, your power supply may have fried completely. Happens fairly frequently, particularly with those cheap supplies that come bundled with cases. Replacement is a reasonably quick process.

Do the fans spin but the initial beep and power-on hardware self-test never starts? Probably major hardware failure on the mobo itself. As the result of heat or any number of reasons.

Power-on self-test starts? Should get a sequence of beeps indicating catastrophic mem, video, or (sometimes) keyboard failure.

But if you can't even get to the video bios screen, or to the hardware bios setup screen, then your hard disk or the contents thereon are the least of your problems.

---

### Post by blkbx on 2010-10-07
I'll jump start it using the front end (crossover the sata cablesand pulling the cfcard) and check the log. NO beeps on the be though no internal speaker doesn't help I guess. Can't remember why or what I did with it. I'll post again aftedr I've gone through the logs. I'll attech if I can find a spare. Thanks for the posts

---

### Post by blkbx on 2010-10-20
just to finish this thread. I got a speaker and finally had time to get  round to installing it. I know, not much to installing a speaker but  mostly it was putting aside time to do it. Making beer came first.  Anyway a single beep about 2 and a bit seconds long and nothing else. No  beeps after that, nothing on the screen either. I 've checked the msi  error codes and this one doesn't seem to show up. If I can get some  spare ram just to check that it isn't the installed set. If that doesn't  give me a better idea of whats going on I think I'll put it to sleep.

---

