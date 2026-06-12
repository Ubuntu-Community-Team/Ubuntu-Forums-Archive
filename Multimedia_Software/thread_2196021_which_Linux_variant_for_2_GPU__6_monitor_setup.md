---
title: "which Linux variant for 2 GPU / 6 monitor setup?"
date: 2013-12-27
forum: Multimedia Software
---

### Post by bluepowder7 on 2013-12-27
I currently have a machine (specs below) that runs fine in Win8.1 for most desktop use, but doesn't work well for watching movies across all 6 monitors, so i'm wondering if there's a Linux OS that handles things better.

 my issue: I can't seem to figure out how to get Win8.1 to play a movie that's stretched across 6 monitors (2x3 grid) smoothly, I get plenty of stutter and low choppy frame rates. I'm 99% sure windows isn't using GPU acceleration and even CPU load isn't more than 20%.

 my system: AMD FX6350 processor, 8G ram, dual HD7790-1GB cards (not crossfired, no eyefinity), 6 monitors (1920x1080 each, three per card)

 my preferred solution: a system that can properly utilize the GPU to decode and display a movie spanning 4 or 6 screens

 really, that's the main thing. for other stuff, the existing setup works fine.

 so, is there a Linux solution that can handle this? I've tried a few things with Win8.1 and nothing seems to work (VLC & enabling its GPU accel feature, 3rd party codecs, other players, etc). heck, I can't even go down to 16bit colour space :/

---

### Post by QIII on 2013-12-27
I have an old HD 5870 using Eyefinity across three monitors under Ubuntu.  I suspect that if I plugged in another and set it up in Crossfire I could span 6 monitors.

Movies across 6 monitors?  You'd have the bezels in the way like muntins in an old window pane.  Pretty irritating.

---

### Post by bluepowder7 on 2013-12-27
to be honest, the bezels are actually far less annoying than the wonky frame rates / stutter / tearing.  I mean, I've had this setup for around 2 years (previously with different hardware and Win7) but have always restricted the movie playing to just 4 screens (cuz engaging the last 2 caused my frame rate to drop to ONE frame per second, if not slower)

if nobody knows (and I wouldn't be terribly surprised as few people overall venture past 2 monitors) then i'll just give the Studio and Xfce versions a whirl and see what they can do without me having to learn a ton of code (I suck at code, i'm a user not a programmer)

---

### Post by QIII on 2013-12-27
It looks like you have to have all the monitors connected to the same card, even if in Crossfire, to get something like a 2x3 going in [SLS mode]("http://www.amd.com/us/products/technologies/amd-eyefinity-technology/how-to/Pages/faqs.aspx#sls-mode-support").

So there's probably not even a solution with a lot of coding.

---

### Post by bluepowder7 on 2013-12-27
crossfire isn't needed, and actually works against me since each card can only support 4 monitors on its own (hence dual non-crossfired cards that each support 3 monitors).  for productivity work, my 6 screens work fine - it's getting the more demanding things to work smoothly that's currently difficult for me to accomplish.

and getting into eyefinity is actually quite a chore even in windows, mostly (only?) because of the ridiculous confusion and lack of clarity as to what is an active versus passive displayport-to-XXX adapter and how one cannot tell simply by looking at the physical part.  the fact that there's even an active-vs-passibe thing is likely why DP isn't everywhere like USB is.  but down the road I might get into this if/when I can manage to have all my monitors with native DP inputs.  I probably SHOULD have done that 2 years ago when I put this setup together, but didn't have the knowledge then that I do now.  :/

there's always the Plan-C which entails just buying a 50"-plus TV, mounting it on my wall, and piping my movies to that.  $500.  maybe $550 if I decide to shove in a third graphics card dedicated for the TV and keep it all within Win8.1

fun fun fun...

---

### Post by bluepowder7 on 2013-12-27
ok, I've tried a few things, and the basic result is:

pathetic.

Ubuntu has zero hope of working.  i'm actually shocked at how bad it is even for basic installation - I first tried Ubuntu when it was at version 7.04 and it worked reasonably well.  now, 13.10 (gnome as well as studio) epically fail at: (1) launching installation in less than 4 resets, (2) recognizing basic keyboard / mouse plugged into rear ports [I had to dig for another keyboard and plug it into front ports just to actually do any install steps, no alternate mouse available], (3) actually RUNNING the installed OS once supposedly done installing (screen full of checks with [OK] but then a refusal to actually show a login screen), and (4) the one time Gnome DID log me in it didn't recognize a single thing and told me i'd have to configure everything myself (key/mouse/monitor/network/etc).  Number 4 was epically funny since it then gave me just one option - restart in safe mode or something along those lines - at which point it would refuse to recognize that spare keyboard I DID have, and effectively called it quits on me altogether.

just for kicks, I tried Fedora.  same results across the board.

wow.  just wow.  if Ubuntu can't recognize a basic keyboard & mouse plugged into the rear ports, it has no hope of recognizing more than 1 graphics card and more than 1 monitor.

---

### Post by Bucky Ball on 2013-12-27
Sorry it didn't work out for you. The majority of other users have no such problems.

On the advice of your last request, at least I think this is what you mean, you've found no joy so:

***Thread Closed.***

---

