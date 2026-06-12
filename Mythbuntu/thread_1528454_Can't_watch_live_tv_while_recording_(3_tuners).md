---
title: "Can't watch live tv while recording (3 tuners)"
date: 2010-07-10
forum: Mythbuntu
---

### Post by SnafuFlux on 2010-07-10
I've got 2 pvr150's and one firewire recording source setup in on the backend.

if I schedule a recording and then try to watch live tv, I can't.  It sits there at the "please wait" screen.

I know in the previous version, it was smart enough to know which tuners were busy and put me on one that was inactive.  

this is a massive flaw, if it cannot detect this now?

help?!

---

### Post by SnafuFlux on 2010-07-10
wow.  I don't know what is going on.

if I set a recording, it chooses the first one available.  makes sense.  I then try to watch live tv, and the system will take me to the "please wait" screen.  then kick back to the main menu.

however, the recording actually changes channels, thus ruining the recording as welL!!

---

### Post by SnafuFlux on 2010-07-10
lol, I'm an idiot!  I had the inputs for my two tuners were both set to /dev/video0

sorry.  delete thread.

---

### Post by Mad_Professor on 2010-07-11
I've made that mistake before, it's okay I think some of us here have done what you did.

---

### Post by Nycest on 2010-08-23
I have a quick question, although it may seem a stupid one for some. I'm just learning about mythbuntu and am extremely interested in implementing it into the house. However, I'm not exactly clear on the idea of mutiple recordings with 1 source.

For example, let's say I want to be able to record 2 shows simultaneously, while being able to watch live tv. I understand I'll need 3 different tuners, but would I need 3 sources (ie., STB's)?? How many tuner cards can I plug one source into?

---

### Post by ozybushwalker on 2010-08-23
In analogue TV you need a tuner per channel.

In Digital TV you can record and watch a number of channels concurrently IF they are on the same multiplex. For example, in Australia ABC digital TV has ABC1, ABC2, ABC3 and ABC 24 on the same multiplex, so it would be possible to watch one of these while recording the other three (if your system, CPU, hard drive etc are up to it).

I have two PCI digital TV tuner cards in the one system. The RF from the antenna is daisy chained through the two cards. A channel scan on the second card picked up fewer channels than the channel scan on the first card. I suspect a lower signal level on the second card but I haven't investigated, partly because what I have got works "well enough". If I recall correctly I have recorded three shows concurrently while watching none. But I haven't tried to push my system to its limits.

A more scalable approach would probably be to use a standard TV signal splitter (1 in, 2, 4 or 8 out) which would quite likely need an amplifier on the antenna side unless you already had sufficient signal strength. Each output from the splitter would feed into a separate tuner card. An experienced TV installer would probably be able to provide good advice on the details appropriate for your location or put together something for you.

---

### Post by Nycest on 2010-08-26
So, in order to have access to all channels at all times with multiple recording, I would have to hook up multiple digital sources. Say for example, I would want to record 1 HBO show, while recording a show on Showtime, while watching a game on ESPN. I would obviously need 3 separate digital sources.

What's the general rule with Cable STBs? Would I need to use 3 stbs?

---

### Post by agamotto on 2010-08-26
Each time you 'split' your antenna lead, you halve the signal.

---

### Post by agamotto on 2010-08-26
> **Nycest said:**
> So, in order to have access to all channels at all times with multiple recording, I would have to hook up multiple digital sources. Say for example, I would want to record 1 HBO show, while recording a show on Showtime, while watching a game on ESPN. I would obviously need 3 separate digital sources.

What's the general rule with Cable STBs? Would I need to use 3 stbs?

If these channels are scrambled, yes, you would need one STB for each channel. If you can watch them on a digital telly with just the coax going into the telly, then you might be able to multiplex record up to 3 at once with a digital tuner.  Analog, unfortunately, will require a tuner and input for each channel.

---

