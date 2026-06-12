---
title: "Why xserver can't display high resolutions on a second screen?"
date: 2010-06-13
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by aviramof on 2010-06-13
The only reason why i prefer to use fglrx it's because on my second screen meaning one of my TV's the 
highest resolution i can use is  1280x720 and with fglrx i can use 1920x1080 i or p if i had that i didn't needed 
fglrx because i don't play games not in linux any way so i don't need to worry a lot about fps so why is that and 
is that something that can be done about it.

Thanks in advance.

---

### Post by aviramof on 2010-06-18
Anyone?

It's quite annoying that the best resolution i can get is 1280x720 when i'm watching 720p tv series and i don't want to switch to windows for that.

thanks in advance.

---

### Post by taavikko on 2010-06-18
> **aviramof said:**
> Anyone?

It's quite annoying that the best resolution i can get is 1280x720 when i'm watching 720p tv series and i don't want to switch to windows for that.

thanks in advance.

720p resolution is 1280x720....

---

### Post by aviramof on 2010-06-18
I meant that the options in monitors(gnome-display-properties)are limited to just three things on my tv screen 1280x720 720x576 720x480 while with fglrx driver i can use every
resolution up to 1920x1080 meaning 1080i or 1080p and it's only on tv's options in my normal screen it's better i don't have all the resolutions that fglrx give me but i only need 1920x1080 
there so there is no problem there.

---

### Post by seeker5528 on 2010-06-18
If you have an older 2.6.34 kernel still installed you could try booting with that to see if it makes a difference.

If you are watching TV series that are 1280x720, don't know why it would be an annoyance that you can't choose a higher resolution, if you were doing other stuff I could understand more.

Are videos actually 'p' or 'i'? I thought the 'p' and the 'i' were just decoding/display options. 

Later, Seeker

---

### Post by Reiger on 2010-06-18
p's are higher quality versions of i's; the i means interlaced, IIRC.

---

### Post by ronacc on 2010-06-18
Reiger	is correct , TV displays can be either P ( progressive ) or I (interlaced) . That depends on your particular TV . computer monitors are all progressive . progressive refers to scanning every line in the display each frame . Interlaced refers to scanning alternate lines in each frame IE odd lines ( 1,3,5 ) in one frame and even lines (2 , 4 , 6 ) in the next frame so that it takes 2 frames to make a complete picture .

---

### Post by aviramof on 2010-06-18
It doesn't matter what kernel i use i had with lucid and with the kernels from then till now 
i have two tv's one is 720p but can show 1080i and the other is full HD but i don't think it
has something to do with the tv's them self because it doesn't matter what tv i connect 
the resolutions options stays the same and i connect the tv's with hdmi cables so the problem 
is no with the connection it's something in the xorg/xserver itself.

---

### Post by seeker5528 on 2010-06-19
I understand the difference between 'p' and 'i' as it relates to a TV. 

I didn't understand

> **aviramof said:**
> It's quite annoying that the best resolution i can get is 1280x720 when i'm watching 720p tv series

Which would imply there were videos that were interlaced or not when they were encoded.

> **aviramof said:**
> It doesn't matter what kernel i use i had with lucid and with the kernels from then till now 
i have two tv's one is 720p but can show 1080i and the other is full HD but i don't think it
has something to do with the tv's them self because it doesn't matter what tv i connect

There does seem to be some discrepancy at the moment. I'm limited to the *x768 resolutions as my highest on one of my systems, since it's not a wide screen 1024x768, but in my case I do get the higher resolutions if I boot with the older kernels.

After being on a waiting list and waiting several days to get a cable box that does HDMI, it's "highest" resolution is 1080i, but after switching back and forth between the 1080i and 720p, the 720p looks better, I don't really consider it to be higher resolution if there are more dots, but clarity is lost. 

The computer we have attached to the TV is not mine, not running Linux, doesn't give 'i' or 'p' options for output, and is mirrored so limited to the computer monitors max resolution of 16xxXsomething, so I can't really compare on that end. The nearest comparison I have is that the 1 TV show so far, that I recorded in Myth TV (with HD Homerun), copied to that computer and played back on the TV did look as good on the TV as it did on the computer monitor at that resolution.

Later, Seeker

---

