---
title: "CPU @ 100% watching live TV, nvidia driver?"
date: 2009-03-27
forum: Mythbuntu
---

### Post by AboveTheLogic on 2009-03-27
Hi all-

I think this is somewhat a noob question, but here goes. I THINK I selected the 177 nvidia driver when I was installing mythbuntu, and I'm guessing its what I need to address.

My CPU is almost always below 10%, but CPU1 (dual core) jumps to 100% when I watch live TV (ATSC Tuner, live TV is HD) and then the remote response slows to a crawl, very unusable.

I'm using a GeForce 9400 GT Video Card, and the machine should be plenty powerful enough (see sig), so I'm sure this can be fixed.

Here are my questions:
How can I check which driver version I'm using with my video card?
How can I change the driver version? Is it likely that the 177 driver is causing the problem?

Anyone have any other info to share?

---

### Post by grytpype on 2009-03-27
> **AboveTheLogic said:**
> Hi all-

I think this is somewhat a noob question, but here goes. I THINK I selected the 177 nvidia driver when I was installing mythbuntu, and I'm guessing its what I need to address.

My CPU is almost always below 10%, but CPU1 (dual core) jumps to 100% when I watch live TV (ATSC Tuner, live TV is HD) and then the remote response slows to a crawl, very unusable.

I'm using a GeForce 9400 GT Video Card, and the machine should be plenty powerful enough (see sig), so I'm sure this can be fixed.

Here are my questions:
How can I check which driver version I'm using with my video card?
How can I change the driver version? Is it likely that the 177 driver is causing the problem?

Anyone have any other info to share?

If your card supports VDPAU, get the packages from avevard.org.

There is a good page on this in the mythtv.org wiki.

---

### Post by AboveTheLogic on 2009-03-27
I'm pretty sure it does. I'll check that out, thanks for the lead!

---

### Post by AboveTheLogic on 2009-04-01
I updated to the newest nvidia drivers (nvidia-glx-180 using the package manager), then added the repositories at avenard.org which eventually resulted in a prompt on my screen asking me to update.

After the update, I'm now running a newer version of Myth frontend that has VDPAU support. This seems to have helped quite a bit, sometimes the CPU cruises around 30% but still has its moments when it spikes.

XBMC as a front end to watch live TV seems to not tax the CPU as much. I think that when mythtv .022 is released that better VDPAU support might come with it that will help this issue.

Its very much usable though, and the new drivers/avenard.org myth update seem to have helped.

---

