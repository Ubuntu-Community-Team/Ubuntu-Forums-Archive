---
title: "Lowest processor speed to play video?"
date: 2009-06-11
forum: Multimedia Software
---

### Post by studentidiot on 2009-06-11
Weird question?

What's the lowest processor speed to play video?

Let's say regular low quality mpegs found all across the interenet? 

Low quality wmvs?

Medium quality - High quality wmvs?

Weird question, but I have a couple of friends, in a computer science class who are trying to port XBMC to the dreamcast and I know nothing about it myself. Seems like there is a huge difference in speed between Xbox and Dreamcast. I think it's pointless

Anyway Thanks!

Also, I can't wait to try out the upcoming release of Ubuntu

---

### Post by mcduck on 2009-06-11
> **studentidiot said:**
> Weird question?

What's the lowest processor speed to play video?

Let's say regular low quality mpegs found all across the interenet? 

Low quality wmvs?

Medium quality - High quality wmvs?

Weird question, but I have a couple of friends, in a computer science class who are trying to port XBMC to the dreamcast and I know nothing about it myself. Seems like there is a huge difference in speed between Xbox and Dreamcast. I think it's pointless

Anyway Thanks!

Also, I can't wait to try out the upcoming release of Ubuntu

Processor frequency ("speed") has absolutely nothing to do with the performance of the processor. It can be only used to compare two processors that are based on exactly the same architecture (which is rarely the case in any real-life situation).

300MHz processor can easily have better performance than a 3GHz processor. It's just a  question of how the processor works, how much data it can handle at a time, how many processing cycles it needs to do a certain task etc.

edit: you could think of it like this: Person A takes 2 steps per second (2Hz) while walking, and each step is 1 meter long. Person B takes only one step per second (1Hz), but has longer legs so his steps are 2 meters long. Both will move forwards at the same speed, even though person A takes twice the amount of steps in the same time..

---

### Post by timzak on 2009-06-11
I've played movies smoothly through Totem on 467 Mhz Celeron.  However, same computer would choke on YouTube because Flash is so resource hungry.

---

### Post by studentidiot on 2009-06-11
OK thanks.

Take for example:

A 200 Mhz MIPS architecture cpu (Dreamcast)

733 mhz pentium 2, which is around what the xbox has. 

What speed pentium/pentium 2 could play sd video? Just curius on this one?

---

### Post by Arup on 2009-06-11
Just to throw an angle, a cheap basic nvidia card with vdpau enabled mplayer will handily outperform a top of the line quad core PC with non vdpau enabled PC. For video performance, a GPU does better than CPU in this case.

---

### Post by wbee on 2009-06-11
Hello,

For what it's worth,I e mailed MSI's technical guys with a question about one of their TV tuner cards.

Their reply,was that for the card,with no other functions open,was at least 2.4 for  good picture,sound,and recording functions.

---

### Post by AoSteve on 2009-06-11
Arup is correct here.   This day in age, the GPU is more important then the CPU.   A good example is my old laptop in the closet.  It's an AMD k6-3 450mhz.    While it "can" play DVD's, full screen it chokes.   I have a desktop machine that's powered by an AMD k6-2 400mhz that can play full screen DVD's all day without skipping.   The biggest difference, the desktop has a Riva 2 nVidia GPU in it.  Even while the laptop has 512mb of ram which is 128mb more then the desktop.

Any basic machine today though should play just about any video you throw at it.  Heck, even my el-cheapo toshiba laptop can play a DVD upscaled to 720P.  :)

---

### Post by mcduck on 2009-06-11
> **AoSteve said:**
> Arup is correct here.   This day in age, the GPU is more important then the CPU.
This is pretty much true for all PC hardware.

But since the original poster was talking about Dreamcast, things are bit different. It's not a PCS, after all, and consoles tend to have very different architecture and roles of different components are not exactly the same as they are in PC world. (Console CPU's are pretty much designed to run handle video, sound and 3D graphics and thus partly do the job your graphics card would do on a PC.). Besides, it's very unlikely that they would be even able to use graphics chip on the Dreamcast for any video decoding.

Based on my experience of running mplayer on a 300MHz MIPS machine I'd say they have pretty good changes of getting good playback for most videos, including MPEG2 and most likely even MPEG4 stuff. However, H.264 will be very unlikely to work. (300Hz MIPS R10000 handles MPEG4 very well but H.264 was too choppy to watch.)

---

