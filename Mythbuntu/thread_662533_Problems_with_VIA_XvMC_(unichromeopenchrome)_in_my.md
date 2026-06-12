---
title: "Problems with VIA XvMC (unichrome/openchrome) in mythbuntu"
date: 2008-01-09
forum: Mythbuntu
---

### Post by rhp on 2008-01-09
Hi all,

I've installed mythbuntu on three systems that have been running mythtv for a couple of years now. First of all: I love mythbuntu! 
Unfortunately, I have a problem with the main frontend, which is a via epia m1000 with a unichrome (cle266) video chip.
The problem is that the CPU seems to be to way to high (compared with e.g. xine, which runs nicely at 10% or so) when using mythfrontend. This also causes problems with lirc: the event from the remote are handled very slowly sometimes (after 10. secs or more).
I've discussed these issues at the openchrome irc list (#unichrome@freenode) and the mythtv-user mailing list ([http://www.gossamer-threads.com/lists/mythtv/users/307135#307135](http://www.gossamer-threads.com/lists/mythtv/users/307135#307135)), but I was unable to resolve the issue.
By now, I am considering going back to mythdora, but I would really love to stick with mythbuntu, since that is running great on the other two systems.
Any help is much appreciated.

Ronald

---

### Post by ozybushwalker on 2008-01-09
G'day,
    You might like to look at a bug I reported, a bug I observed after installing Mythbuntu on a GA-PCV2 motherboard which also uses the CLE-266. There seem to be some similarities with what you are reporting. See [https://bugs.launchpad.net/mythbuntu/+bug/179634]("https://bugs.launchpad.net/mythbuntu/+bug/179634")

---

### Post by rhp on 2008-01-11
Thanks for the suggestion, but I suspect I'm faced with different problems.
My video size gets detected fine:

<dmesg> fb0: VIA VT8623 on 0000:01:00.0, 64 MB RAM
<Xorg> (--) VIA(0): Probed VideoRAM = 65536 kB

One strange thing is that Xorg says it will use 32MB AGP memory (although the size is set to 64MB in the bios):

<<Xorg> (==) VIA(0): Will try to allocate 32768 kB of AGP memory.

Ronald

---

### Post by ozybushwalker on 2008-01-11
Do you know what Xorg video driver you are using? Apparently there is the Xorg "standard" video driver, OpenChrome and UniChrome. Apparently the unichrome driver doesn't support hardware MPEG2 accelerations

What is your desktop resolution? Ist MythTV configured to use the desktop resolution? If so, you may be reverting to software MPEG decode because the CLE266 hardware MPEG decode apparently can handle up to only 1024 (which is more than enough for standard definition  but not enough for HD).

---

### Post by rhp on 2008-01-11
When I first started out, I had the via driver that comes as default. Later I replaced this with the openchrome driver (I did not try unichrome). Both drivers exhibit the same problems.

Ronald

---

