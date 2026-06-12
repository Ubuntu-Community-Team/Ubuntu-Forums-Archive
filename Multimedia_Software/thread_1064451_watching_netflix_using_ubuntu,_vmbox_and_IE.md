---
title: "watching netflix using ubuntu, vmbox and IE"
date: 2009-02-08
forum: Multimedia Software
---

### Post by CeilingCrash on 2009-02-08
The one thing I really missed in ubuntu (ok, the only thing) was Netflix.

A lot of people use Sun's VirtualBox to run XP/Vista *within* Ubuntu,
so they can use IE to watch Netflix.   A very common problem is that the video is too choppy to watch.

I thought I'd share my solution in case it helps somebody out, because i did not see this solution in the various forums i visited.

Long story short - my choppiness went away when i used a wired, rather than wireless connection.   You might think, "well duh, your connection was just too slow."   But my connection isn't too slow - my system also dual-boots natively into XP, where Netflix runs just fine with wireless.   Virtualized under Ubuntu, it was way choppy even tho there was no internet activity from the Ubuntu side.

At first I thought it was video itself that was slow, so I increased RAM to 1 Gb and video memory to 64M.   Made no difference.   Then I noticed that playing a media file on the local drive worked just fine, so I realized it was probably the connection.

I plugged directly into the 'net and presto - Netflix was near flawless.

My guess is this - VirtualBox shares the connection between Ubuntu and XP by *time-slicing* the connection between host and guest OS, allocating 50% of your connection to each (regardless of whether it's being used) by flipping back and forth between OS's.

When Netflix probes your speed, this may occur during an 'active slice' when XP has 100% of the connection, causing netflix to overestimate your real bandwidth capacity by 2.

The wired connection makes up for this by providing >2 times the bandwidth than Netflix needs at highest quality.

I don't know if my theory is correct - it seems like a crazy way to route packets but ... i suppose it would be simpler to implement.  Or, maybe the sharing isn't so crude but rather the guest OS is intentionally throttled to keep the host responsive.

Anyway, perhaps this helps somebody out who's having the same problem.  Just plug directly to the net (and allocate 1 Gb RAM to VBox) ...

---

