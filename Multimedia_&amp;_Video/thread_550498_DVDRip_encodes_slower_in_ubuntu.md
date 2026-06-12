---
title: "DVD::Rip encodes slower in ubuntu"
date: 2007-09-13
forum: Multimedia &amp; Video
---

### Post by meatwad64 on 2007-09-13
I can't figure this problem out and I was wondering if anyone else has noticed something like this happening. 

I tried out CentOS and Fedora recently and they were ok but I liked ubuntu much more. However, while I was playing around with it I took a dvd an encoded it to xvid with dvd::rip and was impressed with it. It encoded pretty fast on my core 2 duo but when i went to try this out on ubuntu i'm getting maybe 1/3 of the speed I was getting with it and I can't figure out why the major difference between the distros. 

Anyone have any idea why the disparity? I can always have another HDD just for this that has fedora but I can't think of why the difference would be so large.

---

### Post by orange2k on 2007-09-14
Well, I use DVDRIP only to decrypt the movie to disk. Later I use Avidemux to do the encoding.
But my machine is rather old and slow and I barely get 4 FPS in second pass.
I don`t know, maybe you used a different codec in Fedora or you may have turned on some advanced filtering option for the encoding process...

---

### Post by meatwad64 on 2007-09-14
I have tried to do the same thing with avidemux and i'm only getting like 15 fps on the first pass instead of 45-50 on my core 2 duo. I think there is something wrong with how ubuntu's kernel is using the cpu. I noticed when i ran the cpu frequency applet my cores were only running at 1.2 ghz instead of using all the cpu speed they have available.

---

### Post by rsambuca on 2007-09-14
Strange.  What version of ubuntu are you using, and what is your current kernel?

---

### Post by meatwad64 on 2007-09-14
I first tried feisty with kernel version 2.6.20 then I upgraded to 2.6.22 and still same thing so then upgraded to gusty just to see and same speed. 

I don't know what to try ? Should i do a fresh format of feisty to see what it does?

---

### Post by rsambuca on 2007-09-14
Have you tried the 64bit version of Feisty?

---

### Post by meatwad64 on 2007-09-14
I haven't tried the 64 bit version. Do you think it will make a difference?

---

### Post by rsambuca on 2007-09-14
Since it can take advantage of the extra registers, it definitely should.  I can attest to the fact that it makes transcoding audio much quicker.  Haven't really done any dvd ripping as of late, though.

---

### Post by meatwad64 on 2007-09-14
Thanks for the heads up i'm going to try that and see how it performs.

---

### Post by meatwad64 on 2007-09-15
Thanks for that hint about trying the 64 bit because now i'm getting the kind of performance I was expecting. 


I would have never thought it would make that big of a difference! But now i'm getting 3-4 times the performance I was getting with 32 bit version.

---

### Post by rsambuca on 2007-09-15
Yeah, it helps if you are using the full capabilities of your rig!  What are you getting for fps rates when transcoding now?

---

