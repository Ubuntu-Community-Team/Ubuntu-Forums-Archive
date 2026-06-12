---
title: "home media network design"
date: 2011-06-22
forum: Multimedia Software
---

### Post by fyra on 2011-06-22
I’m designing and building a home network for a share house. I am an AV tech so running new cable throughout the house will not be an issue.

There are 3 laptops, a PC, potentially a server (I’d need to rebuild it but am willing to spend money there), three HDTVs, 2 xbox 360s and a PS3. There is a modem/router, Cisco 8 port 1000 base-T switch and a Cisco WAP. /deep breath.

I’ve considered a Mythbuntu setup, but I don’t really want to spend the money on 3 nice looking small media computers to run the front ends on. If it is possible to put extra video cards (HD5450 cards are $45 now) into the server and run 1 backend with 3 frontends all at once, perhaps using VNC to control the playback, then I’ll reconsider mythbuntu - but I suspect that even if that is possible, the server’s cpu might balk at decoding three video files simultaneously.

I could use the 3 gaming consoles to play files from the server, but I believe that the issue with this lays with the limited number codecs available on Xbox/PS3 systems. Correct me if I am wrong there.

I’m considering forgetting about rebuilding the server and spending the money on some kind of network storage solution, and then using standalone media players (perhaps the WDTV units) for playback. I could probably get away with that for about $5-600 all up.

I’m asking here for more ideas. I’m willing to spend a bit of money, and I’m willing to put time into building something that will work well. I’m also interested to hear about new purposes that I haven’t thought about yet. 

What else is possible, and what do you think would work the best?

---

### Post by Beacon11 on 2011-06-22
Hmm... I'm actually having trouble picking out a question in there. It sounds like you simply want some sort of media network for running the three TVs, is that correct? And you don't have dedicated computers running the TVs?

---

### Post by fyra on 2011-06-22
> **Beacon11 said:**
> Hmm... I'm actually having trouble picking out a question in there. It sounds like you simply want some sort of media network for running the three TVs, is that correct? And you don't have dedicated computers running the TVs?
No dedicated computers for each TV, correct. The cost of buying them isn’t justifiable. Instead, I can use WDTV players (or some equivalent) which I can buy for under $100 and which can be part of the network.

These are not ideal for playing music from though. So I will need to experiment with that a bit, but I suspect I can use a smart phone for this, and also that the various gaming consoles that may have trouble decoding all video codecs, will not have problems playing the various audio formats.

I have the choice of building a server, or buying a network storage bay with a couple of TB of storage. Neither particularly expensive, but:

Server: A bit more expensive, more power consuming, and more effort required
Network storage: a bit cheaper, uses less power, but is only storage, nothing more.

[I]What are the pros for setting up a server instead? What else can I do with it and why would I choose this option over the other, potentially less flexible solution?
[/I]

---

### Post by BicyclerBoy on 2011-06-22
Non PC frontend soln:
New TVs have DLNA & ethernet connectivity.

MythTV (backend) works as a DLNA server.

Use a tablet/mobile with MythWeb to control scheduling.

Mix:
Run MythTV frontend or XBMC on any or NO computer.
Use a low power PC with GT220/430 or mac mini (nvidia 330M) as a premium frontend for one TV that can then do everything..

Leaves the silly games boxes for what they are best.

The AMD 5450 has bad de-interlacing performance as does GT520.
Neither have enough shader power to run post decode filters.
Both are not recommended for HTPC

---

