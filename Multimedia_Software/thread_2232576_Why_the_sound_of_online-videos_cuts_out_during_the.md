---
title: "Why the sound of online-videos cuts out during their playing?"
date: 2014-07-02
forum: Multimedia Software
---

### Post by dylan0005 on 2014-07-02
Hi Everyone!
I have this audio issue in which the sound of online-videos just **cuts out** while they're playing, the video continues playing with it until it's stop. 
[B]
That's not happen with online-music[/B]! Strength, isn't it? All this problem shows up after a while I'm using the laptop ( about 3 hours kind of) then I just restart the laptop so audio get back to normal. That is Not a solution, I'd like to know **What could it be causing all this audio issue?  **

I'm using Ubuntu 12.04 LTS and Mozilla Firefox. Please help me!

---

### Post by lucianloonstra on 2014-07-03
I guess it could be a lot of things. Can you maybe explain the problem a little more? For instance: what kind of video's are you playing when the problem occurs (more specific: what kind of format)? And when did the problem first occur (was it there since you installed the OS or did it appear after some chanches you made etc.)? What kind of hardware do you have? Et cetera. Maybe I or someone else can help you further if you tell a bit more about these things.

---

### Post by dylan0005 on 2014-07-03
Certainly [I]lucianloonstra
[/I]That's occurs with all formats video, I tried to play in Youtube, tuTV, Dailymotion and others web pages which have videos.
 The problem showed up like a week after I Installed the OS. When I turn on the laptop and start surfing online everything is OK, I mean I can watch videos online without any problem, **BUT** after 3 or 4 hours using the laptop The problem appears.
*Laptop info: 2 GB Ram, 4 GB HDD, Asus Notebook eeepc 900 series*.** Is flashPlayer the cause of this issue maybe? The only thing I did after OS installation was Flash Player upgrade  or could it be anything else?**

---

### Post by lucianloonstra on 2014-07-03
My guess would be that it is a hardware problem. Maybe it has to do with the memory. How much free memory do you have? And how much disk space did you assign for your swap memory? I've also had an eeepc some years ago, more or less similar to the one you're having, but with even less RAM (1 GB) and also only 4 GB space on my HD. Ubuntu has become more resource-hungry over the years I think, which meant that it didn't run smoothly on a netbook with only 4 GB HDD. Maybe you can check how much of your (swap and RAM) memory is being used when the problem occurs. Something that might help (it helped in my case to make it run more smoothly) is freeing up disk space, you can, for instance, remove old kernels (if you haven't done that allready); I suspect you've had some (kernel-)updates since your fresh install. Leaving old kernels on your netbook will cost you a lot of space, around 700 mb, which is a lot on a 4 GB hdd system.

---

### Post by Yellow Pasque on 2014-07-04
This is worth a try (and it's easy to revert if it doesn't help): [https://wiki.ubuntu.com/Audio/PositionReporting](https://wiki.ubuntu.com/Audio/PositionReporting)

---

