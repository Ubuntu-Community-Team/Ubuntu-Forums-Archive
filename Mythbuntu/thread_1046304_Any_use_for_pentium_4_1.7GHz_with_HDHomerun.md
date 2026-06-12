---
title: "Any use for pentium 4 1.7GHz with HDHomerun?"
date: 2009-01-21
forum: Mythbuntu
---

### Post by Dartr on 2009-01-21
I'm very new to the MythTV/Mythbuntu scene and am trying to learn as much as I can as I'm going.  I'm planning to eventually have two machines, one serving double duty as a mythtv and desktop and the other being a dedicated HTPC.  

I'm starting with the following meager hardware:

Pentium 4 1.7GHz
1GB RAM
eVGA 7600GT 512MB AGP
150GB 7200RPM SATA
250GB 7200RPM SATA

This machine performs beautifully for us as a desktop with Intrepid.  To experiment I've loaded Mythbuntu to it just to try out the software (no tv recording/watching yet).

I don't want to invest much, if any, more hardware into this machine.  Using OTA digital broadcasts as my TV source, I need to come up with a system that will be able to handle HD well (record and "live"-watch one program plus record another). The easy parts were the remote and tuner:

Streamzap remote
Silicondust HDHomerun

My plan is to keep the above P4 system as a desktop and add a second machine as the FE/BE that can handle the recording and watching.

With all of the above...

1. Is there any way to utilize the P4 as a FE to watch TV?

2. Would it be possible to build a new FE/BE machine that could downsample on-demand for the P4 without that new machine being overly expensive?

3. Or am I better off ditching the P4 and starting from scratch with two inexpensive dual core machines?

---

### Post by tgm4883 on 2009-01-21
> **Dartr said:**
> 
1. Is there any way to utilize the P4 as a FE to watch TV?

No

> **Dartr said:**
> 
2. Would it be possible to build a new FE/BE machine that could downsample on-demand for the P4 without that new machine being overly expensive?/QUOTE]

No

[QUOTE=Dartr;6590733]
3. Or am I better off ditching the P4 and starting from scratch with two inexpensive dual core machines?

No, you could use the machine as a dedicated backend, but you are not going to play any HD content on that thing.  Maybe, just maybe, VDPAU might help you, but i'd just make that a backend only machine.  It should have no problem recording the HD content and can also flag recordings for commercials

---

### Post by Dartr on 2009-01-21
> **tgm4883 said:**
> ...i'd just make that a backend only machine.  It should have no problem recording the HD content and can also flag recordings for commercials

Hmmm...I haven't considered that option.  So if I understand this right, a backend-only machine does not need much of a processor or video card.  Just space and access to a tuner and network?

Would this machine be able to support 2 (or more) front-ends streaming the HD from it?  Again, it sounds like this P4 in a backend only role would only be utilizing the disks and not the processor, right?

---

### Post by tgm4883 on 2009-01-21
Yea it should be able to handle a couple frontends off of it.  The main thing would be the disk io, your best bet is to just try it, but it shouldn't be too much of a burden on the system since it is just reading from and writing to disks.  The commflagging (to mark where commercials are) would work well on this machine in conjunction with the previous work.

You don't need much of a video card at all (integrated is fine), and CPU wise shouldn't need much either.  Your main CPU tasks would be commflagging and mysql stuff.

---

### Post by newlinux on 2009-01-21
I agree with tgm4883. But VDPAU won't support that video card, so that isn't an option. You could try XvMC. With XvMC you might be able to get it to play mpeg-2 HD. I've seen others with similar CPU get HD working with XvMC. 

[http://www.mythtv.org/wiki/XvMC](http://www.mythtv.org/wiki/XvMC)

---

### Post by blairm on 2009-02-13
sorry, wrong place to post

---

