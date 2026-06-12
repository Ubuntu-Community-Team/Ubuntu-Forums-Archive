---
title: "No /dev/video0 in Intrepid Ibex"
date: 2008-11-24
forum: Multimedia Software
---

### Post by DarthSudaka on 2008-11-24
Hi!

I have a PCI tv tuner card (Flyvideo 98 - bt878 ) which was working flawlessly in my ubuntu 8.10 updated from 8.04.

I changed my HDD so I did a fresh install of 8.10, and now it does not work at all.  :(
Both tvtime and xawtv say they can´t open /dev/video0
Checked and, in fact, there`s no /dev/video or /dev/video0.

lspci does show the "brooktree" capture device, so I guess ubuntu did recognize the hardware, right?

What can I do?? 

Thanks a lot!!

---

### Post by dchurch24 on 2008-11-24
Have you tried VLC, if only because IMO it has better logging.

May be you could try moving it to a different PCI slot.

Without more info, I am guessing.

---

### Post by annda on 2008-11-24
to see if your card has been registered under a different device name, try

```
dmesg | grep bttv
```

check the output for any error messages

---

### Post by DarthSudaka on 2008-11-30
I changed it to another PCI slot and worked.

Thank you both!!

---

### Post by dchurch24 on 2008-12-02
I'm guessing it was some kind of IRQ conflict - or maybe a conflict that arose from upgrading rather than installing from scratch.

Every six months, instead of upgrading, I start again from scratch - all my important stuff is held on an external NAS so it's nice and easy.

That's just me though - I like to install the latest straight away.

---

