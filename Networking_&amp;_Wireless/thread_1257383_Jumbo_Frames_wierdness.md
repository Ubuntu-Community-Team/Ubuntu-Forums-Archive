---
title: "Jumbo Frames wierdness"
date: 2009-09-03
forum: Networking &amp; Wireless
---

### Post by arius13721 on 2009-09-03
Hopefully someone can shed some light on a problem I seem to be having. I'm running gig ethernet in my house, but whenever I crank the MTU to 9000 on my network card, I get some weird issues. 

It seems that once I put it to anything over 1500, it will "drop" off the network if traffic with any substance traverses the interface. For example, with the MTU at 1500, I can perform a dmesg no problem however, when I raise the MTU, I will get back some data, and it will appear to hang the box. At that same time though, I am able to ssh right in without any problems.

There is nothing of help to be found in syslog indicating why this is happening. My network card is an integrated nvidia nic and it's using the forcedeth kernel module. Additionally, I'm using 64bit jaunty.

---

### Post by jonobr on 2009-09-03
Interesting,
Sounds like as if your GE card would prefer lesser MTU size then 9000.

Im guessing your other device which connects via ssh is doing so at a lesser negotiated MTU?

What is the exact make of card? There may be something on related forums regarding Jumbo frames?

---

### Post by dbalascak on 2009-09-03
All elements in the layer 2 path between the source and destination need to be capable of Jumbo frames.  The local switch(es) will limit the size of packet unless it too supports an MTU of 9000.  Confirm that the switch is capable of the same MTU size.

---

### Post by jonobr on 2009-09-03
Hey dbalascak

I haven't worked much with Jumbo frames, but shouldn't the GE compensate for the switch that doesn't support Jumbo and throttle back accordingly?

Again, I don't have a lot of operational experience in this field.
Mostly theory..

---

### Post by arius13721 on 2009-09-03
I've tried at other MTUs as well.. 5k & 7k. Similar results. Additionally, when I'm ssh'd in, and have the MTU cranked up, if I have multiple terminals (from the same box) the one that is transferring a "large" (as large as the output of dmesg is) amount of data hangs, but I can continue to execute commands from a different terminal at the same time.

As for the nic it's integrated onto the motherboard which is an xfx 780i.

---

### Post by arius13721 on 2009-09-03
> **dbalascak said:**
> All elements in the layer 2 path between the source and destination need to be capable of Jumbo frames.  The local switch(es) will limit the size of packet unless it too supports an MTU of 9000.  Confirm that the switch is capable of the same MTU size.

Hrmm.. yes, I overlooked this. I just assumed (my bad) that because it was a GB router, it would be capable of jumbo frames. Right now it is definitely not capable, as I just verified, but I don't yet know if it's an issue with the router itself (wrt310n) or the firmware (ddwrt).

---

