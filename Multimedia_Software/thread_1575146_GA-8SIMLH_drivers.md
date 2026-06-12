---
title: "GA-8SIMLH drivers"
date: 2010-09-15
forum: Multimedia Software
---

### Post by CoreOxide on 2010-09-15
Heya,

Where can I find graphics (and other needed?) drivers for this MoBo?

Regards.

---

### Post by Yellow Pasque on 2010-09-15
They're built into the kernel...

---

### Post by CoreOxide on 2010-09-15
Is there an update \ additional software i need to install?

Even youtube videos are stuttering. When I was using Win XP it was fine.

---

### Post by Yellow Pasque on 2010-09-15
What graphics card do you have?
```
sudo lshw -C multimedia
```

---

### Post by CoreOxide on 2010-09-15
>  description: Multimedia audio controller
       product: AC'97 Sound Controller
       vendor: Silicon Integrated Systems [SiS]
       physical id: 2.7
       bus info: pci@0000:00:02.7
       version: a0
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=Intel ICH latency=32 maxlatency=11 mingnt=52
       resources: irq:18 ioport:d800(size=256) ioport:dc00(size=128)


Here is the result, but as far as I see it's the sound card...
The driver I used in windows was SiS 651, if this helps.

---

### Post by cascade9 on 2010-09-15
Flash is always worse on linux than it is in widows...and that SiS video controller isnt helping much at all. :( 

Any cheap 2nd hand computer places near where you are? Picking up a cheap nVidia geforce would help a fair bit.

---

### Post by CoreOxide on 2010-09-15
Will do.
Thanks Man ;)

---

### Post by Yellow Pasque on 2010-09-15
Oops, Should have been lshw -C video, but yes, SiS Linux drivers are severely lacking.

---

### Post by cascade9 on 2010-09-15
> **Temüjin said:**
> Oops, Should have been lshw -C video, but yes, SiS Linux drivers are severely lacking.

doh! 

I missed that as well.....too tired from excessive amounts of hardware poking today.

Anyway, I guess it would be the onboard SiS video that is running. Thats just a guess though, posting your lshw -C video isnt a bad idea- Temüjin would have a much better idea of how to improve it without buying hardware, if I hit trouble with onboard VIA/SiS/Intel video I just walk out to the parts bin and find a suitable card......

---

### Post by Yellow Pasque on 2010-09-15
It's an AGP slot, so finding a video card might be a bit of an adventure.

---

### Post by cascade9 on 2010-09-15
> **Temüjin said:**
> It's an AGP slot, so finding a video card might be a bit of an adventure.

I dont have any issues finding AGP cards. Not that I need to, I've got more than afew AGP cards in the parts bin, but I can get AGP MX-4000s for $10 AU (about $9 US) from one of the shops here.  

I'm probably not typical though.

---

### Post by Yellow Pasque on 2010-09-15
Yeah, but a better video card might not be the answer since Flash is unaccelerated on Linux (unless it's the SiS drivers causing the issue).

A CPU upgrade might be better :\

---

### Post by cascade9 on 2010-09-15
> **Temüjin said:**
> Yeah, but a better video card might not be the answer since Flash is unaccelerated on Linux (unless it's the SiS drivers causing the issue).

A CPU upgrade might be better :\

Agreed, on both counts. Well, in part anyway..... I read "Even youtube videos are stuttering" and thought that youtube was just part of the problem, not the only issue. I know when I've tried using a SiS card everything has been laggy as hell, and that was a better card (an actual card for a start!) than the siS651 IGP. 

True, CPU upgrade would probably help as well, but that would depend on what CPU is currently in use.  I find that its harder and more expensive to get older Intel CPUs than video cards.

---

