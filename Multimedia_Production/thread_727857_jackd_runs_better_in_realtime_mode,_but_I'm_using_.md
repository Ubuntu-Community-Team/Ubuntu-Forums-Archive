---
title: "jackd runs better in realtime mode, but I'm using the generic kernel"
date: 2008-03-18
forum: Multimedia Production
---

### Post by abalone on 2008-03-18
**JACK** runs in realtime mode even though I use the **linux-generic** kernel. 

IIRC - It wasn't doing that "back then" - before there was a **linux-rt** package (or before I knew of it)! Back then it refused to run in realtime mode, just like it refuses to run at 192 kHz on my onboard sound chip. [SIZE="1"](Why *does* it have to impose the sound hardware's limits on a software setup...?)[/SIZE]

It does seem to make a difference, too: "Realtime" box checked: no xruns except on startup at 128 frames/period. CPU usage stays at about **0.5%** when idle. "Realtime" box unchecked: occasional xruns, CPU usage starts vacillating, reaching **10%** while doing nothing. (Both with linux-generic kernel. Ever since an upgrade to a dual core processor I can't boot into the realtime kernel anymore - everything goes haywire/becomes unresponsive/dies as soon as something's demanded of the CPU, and I can only push the reset button to get it back to normal.)

This situation would be fine if only **Rosegarden** got along better with the linux-generic kernel. System timers too low-res... 

What's happened? Has the installation of the -rt kernel accomplished something that remains effective even when not using said kernel?

---

### Post by alecz20 on 2008-03-18
On my system, I noticed more xruns with Realtime mode than without it.

However in Realtime mode the xruns look like this 5(46), and without realtime mode they look like this 5(5). Not sure what is the difference, but it is not noticeable!

Any ideas?

---

### Post by abalone on 2008-03-21
Just upgraded to 7.10 64 bit - rt kernel still dies on me, as before. :-? (As does JAD's rt kernel. PCLinuxOS' rt kernel doesn't.) 

Also as before - JACK runs better in rt mode (on the non-rt kernel), at least if the QJackCtl display is to be believed.

> **alecz20 said:**
> On my system, I noticed more xruns with Realtime mode than without it.

However in Realtime mode the xruns look like this 5(46), and without realtime mode they look like this 5(5). Not sure what is the difference, but it is not noticeable!

Any ideas?

Not me, sorry...

---

