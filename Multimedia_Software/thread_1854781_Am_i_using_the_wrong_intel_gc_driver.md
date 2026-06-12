---
title: "Am i using the wrong intel gc driver?"
date: 2011-10-05
forum: Multimedia Software
---

### Post by Larswa on 2011-10-05
Hi,

Just installed the latest Ubuntu 11.10 Beta, and have been running it for a couple weeks on my Thinkpad T410S
My first venture into Ubuntu, and I like it..

The machine has the first generation Intel HD Graphics that came with the Arrandale i3/i5/i7 mobile series.  

BUT the driver seems to be a i915 driver, which I do not understand ... Is there something I should do, post install to get a newer driver?  I am NO unix guru, so be gentle :-)

The graphics are okay - Unity and Compiz crashes are frequent, but not so frequent that I blame the graphics driver. I've been playing with KDE, and that is blazingly fast as well .. so everything seems to be working. But a 3-4 year old driver for a 1 year old card??

I've been through the forums, but didn't find the answer. And I am hesitant to just add any new source for my update-manager...

---

### Post by mikewhatever on 2011-10-05
i915 is not 3-4 years old, it gets updated by Intel about twice a year. I don't think you have anything to worry about.

---

### Post by Larswa on 2011-10-05
Hi - thanks for your response.

And it IS working. And I know I'm gonna break it if I mess around :-)

But maybe someone should change the name of that driver?   the "i915" is the naming for the chipset - not the GMA chip. 

And the i915 chipset is about 5 generations old, if you only count the mobile chipsets that intel has released. If it should be aimed at the generation of intel chipsets, that include the HD driver, I would have expected it to to be named something else!?

For reference, check the intel GMA / chipset information here:
[http://en.wikipedia.org/wiki/Intel_GMA#Table_of_GMA_graphics_cores_and_chipsets](http://en.wikipedia.org/wiki/Intel_GMA#Table_of_GMA_graphics_cores_and_chipsets)

---

### Post by mikewhatever on 2011-10-05
Try [http://intellinuxgraphics.org/feedback.html](http://intellinuxgraphics.org/feedback.html), mabe they'll listen.

---

### Post by Larswa on 2011-10-05
I'll give that a try. Good suggestion, thanks.

---

### Post by collisionystm on 2011-10-05
Intel already packages there drivers in the Linux Kernel. Running the latest kernel means you are running the latest Intel Driver. I already investigated this recently because I was wondering the same thing about my computer.

---

### Post by Larswa on 2011-10-05
Hi Collision,  thanks for your reply.

That's about what I could figuer out after reading as well ... I just don't like them listing the driver as an i915 chipset driver. That is a driver for the GMA 900 grfx chip, and I remember having one of those back in 2005 or 2006.  

But never the less thanks for your reply!  I give in and give up :-D

---

### Post by Larswa on 2011-10-05
Hi Collision,  thanks for your reply.

That's about what I could figure out after reading as well ... I just don't like them listing the driver as an i915 chipset driver. That is a driver for the GMA 900 grfx chip, and I remember having one of those back in 2005 or 2006.  

But never the less thanks for your reply!  I give in and give up :-D

---

