---
title: "is it kwin or intel?"
date: 2010-08-28
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by x-shaney-x on 2010-08-28
Testing maverick KDE has been horribly unstable.
Apps are crashing left right and centre and if I change any settings in system settings it instantly crashes virtually every running app when I click "Apply".

For the past couple of days I have been running compiz instead of kwin as window manager (with emerald since kde4-window-decorator won't run) and everything has been much more stable and performance-wise, a huge improvement.
I notice the "big" effects such as blur and transparency run perfectly on compiz but have major problems with kwin (blur won't actually blur at all with kwin).

Disabling kwin effects does improve stability a lot but still doesn't run as well as compiz.


Also, with or without desktop effects, dolphin cannot run more than a few seconds without crashing, even when it is just open doing nothing and I'm working on something else it will just crash for no apparent reason.

So are these problems actually down to kwin or is there problems with the intel driver in particular running kwin?

---

### Post by ranch hand on 2010-08-28
As I do not run Kubuntu I can't answer your question.  I would. however, think that very likely.

I just hope you have filed some bugs on this.  There seems, to me, to be a very strange reluctance to file bugs no the part of kubuntu users.  Don't know why but but would think that this has to do with the poor condition of Kubuntu at final release compared to Xubuntu and Ubuntu.

I do realize that you are one of the people who probably does file bugs but Kubuntu users seem better at complaining than filing bugs.

---

### Post by VMC on 2010-08-28
A better forum for Maverick Kubuntu is Kubuntu.net forums, found [here]("http://kubuntuforums.net/forums/index.php?board=124.0").

Right now I'm using Kubuntu Lucid, and love it. I've tried many others, but I find the underlining similarity between Ubuntu to be of great help. There's a  lot of knowledgeable people on that forum willing to help.

Since I'm not running Maverick Kubuntu I can't be of much assistance.

---

### Post by Reiger on 2010-08-29
It's probably not KDE but an underlying Qt library that segfaults. Anyway, I only have an occasional crash. Pretty stable if a little sluggish to shutdown.

---

### Post by bennachie on 2010-08-29
Kubuntu Maverick (32-bit version) is running very well for me, both on my laptop and on my desktop machines. The user community appears to be smaller than for vanilla Ubuntu, which lends weight to the advice to lodge bug reports as soon as it is clear that the issue is a real one.

For my money, Kubuntu Maverick is already the nicest KDE distro around, having overtaken the long-term leader, openSUSE, so a concerted effort to identify and report as many bugs as possible at this stage should be well rewarded. I suspect that the user group will become much larger once 10.10 is released and the broader KDE community realises that Kubuntu is no longer the poor cousin.

---

### Post by x-shaney-x on 2010-08-29
@ ranch hand
Haven't filed any bugs for kubuntu as of yet since I have only just started trying it and at the moment trying to figure out where the problem lies because I think it might be a bit too vague to be very helpful just now.
This will sound a bit stupid I know but I never even thought to look for a kubuntu forum, I just assumed it would be part of this one :)

This issue is on an ubuntu GNOME maverick install with KDE installed afterwards.
Last night I installed the maverick kubuntu alpha 3 iso to compare and have exactly the same problem.

Now, to confuse matters more, I have been playing around with mint 9 KDE and I have upgraded it all to maverick (busy night last night :) ) after removing the mint sources and not suffered a single crash on that one.

Since I also upgraded the kernel and removed all the mint tools it is to all intents and purposes now kubuntu maverick and I haven't suffered a single crash of any kind, not even the non-stop dolphin crashes.
So not exactly sure what that tells me yet.

---

### Post by x-shaney-x on 2010-08-29
I think my problems may well be related to this: [http://osdir.com/ml/kwin/2010-08/msg00449.html](http://osdir.com/ml/kwin/2010-08/msg00449.html)

---

### Post by VinDSL on 2010-08-29
> **x-shaney-x said:**
> I think my problems may well be related to this: [http://osdir.com/ml/kwin/2010-08/msg00449.html](http://osdir.com/ml/kwin/2010-08/msg00449.html)Interesting!  Good job, detective...

I have an ancient e-tower (circa 1999) that a co-worker donated to my collection.  It has an equally ancient Intel chipset, so I'm always interested in these kinds of threads.  

Ubu was a no-show.  But, I'm successfully running MacPup Opera 2.0 (Puppy Linux 4.3.1 with an E17 desktop) on that machine.  

Anyway...

There was a link at the top of the page you provided:  [https://bugs.kde.org/show_bug.cgi?id=241402](https://bugs.kde.org/show_bug.cgi?id=241402)

Reading through the comments, it certainly *sounds* like the problem(s) you're experiencing.  

This is probably the most succinct: [https://bugs.kde.org/show_bug.cgi?id=241402#c60](https://bugs.kde.org/show_bug.cgi?id=241402#c60)

You might want to check it out, if you haven't done so already.  ;)

---

### Post by x-shaney-x on 2010-08-29
That certainly seems to be the problem I'm having.
Doesn't look like there's a lot I can do about it.

I'm starting to get used to KDE now and will probably stick with it but stay with < 4.5 til these issues are resolved.

---

### Post by buzzmandt on 2010-08-29
intel vid here, maverick kde 4.5 works ok for me, but not from the start. i have to uncheck use effects and apply, then recheck effects and apply for it to run right.  after that it's great....

running kde 4.5 on lucid for my main and works fabulous.

---

### Post by krazyd on 2010-08-29
> **ranch hand said:**
> I just hope you have filed some bugs on this.  There seems, to me, to be a very strange reluctance to file bugs no the part of kubuntu users.  Don't know why but but would think that this has to do with the poor condition of Kubuntu at final release compared to Xubuntu and Ubuntu.A common misconception, both on the bug-filing and on the quality of the Kubuntu release.

> **ranch hand said:**
> I do realize that you are one of the people who probably does file bugs but Kubuntu users seem better at complaining than filing bugs.

I hardly ever file bugs on Kubuntu itself because Kubuntu uses packages with very few changes from upstream, which means that it is much more useful to report bugs upstream and wait for fixes to flow downstream in the next minor release.

---

