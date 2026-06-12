---
title: "dual core slowdown with file copy"
date: 2008-02-20
forum: Multimedia &amp; Video
---

### Post by clickwir on 2008-02-20
I'm going to try putting this simply.

I have a dual core machine and Gutsy Kubuntu see's the both cores just fine.

However, if I start a large amount of file transfers... say from one internal SATA drive to another, or from an internal drive to an external via USB. What I see is that the whole system gets choppy, even though only one core is partly used. Maybe 60-90% use on one core. The other is 0-5%.

Just trying to play a YouTube video is choppy. I'm attributing it to not being cpu load balanced well. While doing this file copying, and playing the video, I'll notice the first core is 100% and the second is 10-20%. 

My logic tells me that let the file copy use one core and don't use up the rest of the first core, but switch to the 2nd core for the new thread instead of using a little of both and giving poor performance.

To be honest, it's not just the file copying that I see this with. If anything is using the majority of one core, the next thread that needs a good amount of cpu time seems to eat up the remainder of the first core and part of the second. Instead of just going completely to the second core.

I doubt there's much that I can do about this, but I thought I'd put it out there just in case there might be.

---

### Post by Existentialist on 2008-02-21
How much RAM does your system have?  If you don't have a sufficient amount of RAM, the system is having to use swap, and if this is on the same drive that you are reading or writing to the system will become noticeably slower.

---

### Post by anindya_m on 2008-02-21
Hi, are you sure DMA is turned on for all the drives? Maybe you can try running
```

dmesg | grep -i dma

```
after the system has booted.

---

