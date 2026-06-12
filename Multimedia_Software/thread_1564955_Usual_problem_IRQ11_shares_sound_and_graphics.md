---
title: "Usual problem: IRQ11 shares sound and graphics"
date: 2010-08-31
forum: Multimedia Software
---

### Post by Royke on 2010-08-31
Hello fellow Ubuntero's,

It is almost done on this machine, the system is pretty well configured for realtime audio. There is only one big clinch left and i still can not understand the tutorials about setting up IRQ.
Is it , or is it not possible to change IRQ by software??
What i want to reach is a seperate IRQ for my onboard alc888, wich has proven to be not so bad after all(not to talk about pulseaudio!) Or maybe shift IRQ of the graphics card??

I can not believe this isn't possible in 2010 and i want to do every effort there is to set this up right, even if it takes shortcircuiting and soldering, or must i buy an external firewire audiodevice, with the risk it just goes into IRQ11 again.
I tried to shift pci-IRQ and it works although i can't find the logic in here. It seems to change every IRQ in a stange order, but not 11.

For now i'm lucky that it works this well, there are only accidential xruns and most of them i can't even hear or messure when zooming out a recording a thousand times. I would dare to take my pc on stage now(hidden in a case)

I do wander why the manufacturers of mainboard come up with the idea to share audio and graphics on the same channel, it feels DRM to me. We don't eat and *** at the same time either:D

---

### Post by Royke on 2010-09-05
I'm sorry Ubuntu for posting this thread. But now that it's here i will post here my findings on this, It is now only this problem i'm working on so i expect to finally learn. Please be patient with some of us ):P

---

