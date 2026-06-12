---
title: "Force 4k 15fps on old pc with new display"
date: 2021-01-30
forum: Multimedia Software
---

### Post by eatbigliftbig1 on 2021-01-30
I've been trying for days to get 4k output on my 4k tv from an old laptop that by default outputs in 1080p

I don't need 60 fps even 15 would be great

I've used xrandr to set a custom 4k resolution but that only allows me to see 1/4 of the screen the other 3/4 are off screen.

Please help me with this lol I'm desperate. I'm trying to build a blogging machine for my old father and he can't see well in 1080p

---

### Post by QIII on 2021-01-30
How old is the laptop?  What is the OEM and model of the GPU?  What is the maximum resolution the GPU can output?

The GPU can only do what the GPU can do, despite what you may have it connected to.  If you have a spigot on the side of the house that can deliver 5 gallons per minute through a common garden hose, you cannot attach a fire hose and expect to get anything more than 5 gallons per minute to your garden.

---

### Post by eatbigliftbig1 on 2021-01-30
I'm definitely going to get that info when I go over there tomorrow. However I have seen 4k output on a raspberry pi 2... unfortunately the pi doesn't support wordpress desktop since it's arm

---

### Post by QIII on 2021-01-30
Some 1080p graphics hardware can do 4k -- sort of.  4K is 4 times the area of 1080p.  That means roughly 1/4 the FPS (actually less due to processing latency, but we'll go with 1/4)

So what you may have seen as an RPi2 doing sort-of-4K at < 15 FPS.  If your Dad is just reading documents, that would probably be fine.  Watching news videos ... not so much.

But that depends on the hardware.  Such trickery is not always possible.  That will depend on the hardware the machine has.

---

### Post by eatbigliftbig1 on 2021-01-31
My graphics processor is the Intel bay trail.
Processer is pentium r cpu n3540 2.16ghz x 4

---

### Post by CelticWarrior on 2021-01-31
This answers your question:
[https://community.intel.com/t5/Embedded-Intel-Atom-Processors/Bay-Trail-Z37xx-Max-Resolution/td-p/264113](https://community.intel.com/t5/Embedded-Intel-Atom-Processors/Bay-Trail-Z37xx-Max-Resolution/td-p/264113)
In summary, the embedded graphics supports 4K only with a DP connection and that is notoriously absent in the cheap Celeron based laptops of that era.

---

