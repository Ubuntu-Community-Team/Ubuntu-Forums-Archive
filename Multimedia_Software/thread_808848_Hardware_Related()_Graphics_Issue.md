---
title: "Hardware Related(?) Graphics Issue"
date: 2008-05-26
forum: Multimedia Software
---

### Post by dbsoundman on 2008-05-26
I'm having a strange issue that I at first thought was my OS, but seems to be at least cross-generational in terms of OS releases. Currently I'm using Ubuntu 7.10 and having this issue, but I also had it when I tried 8.04 for a while. Here's what the symptoms are: when I am running either Google Earth, Xine (dvd play in general), or using the Metacity system, my graphics card ATI Radeon 9250 seems to crash. My screen either goes black, into powersave mode, or it says "input not supported". Sometimes with Google Earth instead of crashing it will start making random patterns all over the screen, and if I close the program the problem disappears. Usually though I cannot do anything but RSEIUB when it appears because ctrl-alt-backspace will not usually work either, but sometimes it will. If, for example, I'm watching a movie, the audio will sometimes keep playing as well. In terms of basic functions, so long as I use compiz and NOT metacity, everything is fine, which is really strange since compiz is more graphics-intensive.

The main reason I got this video card in the first place is to support my 20" widescreen LCD monitor, so I'm not that tied to it so long as I have something that works with that resolution, but at the same time I'd rather not just go buy a new card and see if that works better. I almost wonder if I'm having heat issues, as the way my PCI setup is oriented the card actually goes in upside down, so the heatsink (which has no fan) is on the bottom instead of on the top. I don't know if this is actually the issue or not.

I have not yet tried a completely different OS on this machine yet, but I suppose if I must, I must. I have a feeling it will be the same though. FWIW; the machine has an AMD Athlon XP processor, I don't know the motherboard type; I believe it has 1GB RAM, and two hard drives; one I think is 30 GB and the other is 200 GB if I'm not mistaken (I'm quoting this all from my head).

Anyone have thoughts/suggestions?

Thanks,
Dan

---

### Post by dbsoundman on 2008-05-31
No one? I'm out of ideas here. The only thing I can think of otherwise would be to check into the motherboard and maybe get a better one...? I don't know what the one I have is, or how good it is...

-Dan

---

### Post by Kevbert on 2008-05-31
First thing to try would be to run memtest, from the grub menu, to check your mobo ram.  It looks like your running some memory intensive programs.
It may be that the board is overheating.  Make sure any other PCI boards etc are as far away from that card as possible.  Does the fault occur immediately after turning on the PC (and running these applications as soon as possible)  ?

---

### Post by dbsoundman on 2008-05-31
I do have one other PCI card, an M-Audio Delta 1010 soundcard, which I could move down one slot I think. I will try tomorrow morning when my computer is cooled off and see if I can run those programs without problems...I did run memtest before (a month ago at most) when this problem was first appearing and I didn't get any errors.

-Dan

---

### Post by Kevbert on 2008-05-31
When you run memtest, please run it for at least an hour.

---

### Post by dbsoundman on 2008-06-02
I tried running Google Earth right after startup, and I still had the same issues; with Google Earth it's sort of a gradual thing; I can use it for a little while, but random bits of the screen become randomized, and eventually it crashes. I also ran memtest yesterday for like an hour and a half and it showed no errors.

One other thing I realized is I think this issue appeared after I did an OS fresh install. I was having problems with my previous 7.04 installation (non-graphics issues), so I did a fresh install of 7.10 and had this constant graphics freeze (which I later found was metacity), so I installed 8.04 beta, and had the same problem. I switched to compiz, and had no problems with basic programs, but I had not installed google earth, nor did I watch any DVDs or anything like that while I had that installation. Now I'm back to 7.10 after I accidentally destroyed my 8.04 install. So, it's possible that this problem is related to a combination of issues, one of the factors being some sort of software change after 7.04. I have a feeling I have hit a dead end.

Is there some way to find out what my motherboard is, it's possible that I have a crappy one I could change out...what else can I try?

Also, I copied down some specs when I ran memtest if this is helpful:

Athlon XP (0.13) 1808 MHz
L1: 128K 11090 MB/s
L2: 256K 3530 MB/s
Memory: 1024M 527 MB/s
Chipset: VIA KM266


-Dan

---

