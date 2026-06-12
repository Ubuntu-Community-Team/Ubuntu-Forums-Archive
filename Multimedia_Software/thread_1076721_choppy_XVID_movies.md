---
title: "choppy XVID movies"
date: 2009-02-21
forum: Multimedia Software
---

### Post by tudor_victor on 2009-02-21
Hello,

I have just installed Ubuntu 8.10

Totem automatically installed the codecs to play AVI/mpg/mkv etc.
The problem I have is that some videos are "jumpy" while others are very smooth. some of the jumpy videos have very obvious frame skips.

I installed VLC and those videos that are very jumpy in Totem are much better in VLC but you can still see they are not perfectly smooth.

I tried to find out if it was a specific codec that was causing the problem and it seems most of the videos that are choppy are using XVID. However I do have some XVIDs that are smooth. I also have some DIVX MPEG-4 videos that are jumpy but found others that are smooth.

These videos were playing fine in windows.
I have an ATI Radeon 9800Pro video card. I tried with both the ATI proprietary drivers and the standard Ubuntu drivers, makes no difference.

What could be the problem?

---

### Post by dm_fw on 2009-02-21
I had the same issue.  Files that are highly compressed, ex. MPeg4, required a processing power for smooth viewing.  Check background tasks and low memory.

---

### Post by tudor_victor on 2009-02-22
I checked.

memory is not an issue, I am at most using 450 megs out of 2 gigs of RAM and nothing of the 5 gigs of swap.

the CPU is another story. CPU is at 100% when totem is running. Totem is taking 70 to 80% of the CPU time and the rest is taken by Xorg

when VLC is showing the same movie it only takes at most 50% of CPU (30% less than totem on average) and the CPU is not used more than 70% which I guess explains why VLC is smoother.

So my question is, why is Totem using 70 to 80% of the CPU when VLC only needs at most 40-50% for the same movie?

Also, why is Xorg taking 20% of my CPU and how can I reduce that?

---

