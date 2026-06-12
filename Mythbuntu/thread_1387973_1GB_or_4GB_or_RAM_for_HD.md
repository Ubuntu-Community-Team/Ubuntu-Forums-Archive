---
title: "1GB or 4GB or RAM for HD"
date: 2010-01-22
forum: Mythbuntu
---

### Post by jquintana on 2010-01-22
I am using an AMD Athlon II X2 250 (3.0Ghz) and an Nvidia GeFOre 9400GT (1GB) along with a Hauppauge HD-PVR. 

My current dilema is whether to stick to 1GB or upgrade to 4GB or RAM in order to have a clean HD capture/display.

I was running with 1GB and was seeing some "lines" (not sure what it is called) when watching fast-moving shows such as an NBA game yesterday. I thought it was because of my low RAM so I upgraded to 4GB but was still seeing the same "lines".

Do I need the additional RAM for a front/back-end machine? I will eventually be adding more front-ends to my system.

Thanks!

---

### Post by LowSky on 2010-01-22
if your added more front ends then yes... without seeing what those "lines" looked like it hard to say what is to blame? But off the top of my head, I hope your using the proprietary nvidia driver.

---

### Post by klc5555 on 2010-01-22
> **jquintana said:**
> I am using an AMD Athlon II X2 250 (3.0Ghz) and an Nvidia GeFOre 9400GT (1GB) along with a Hauppauge HD-PVR. 

My current dilema is whether to stick to 1GB or upgrade to 4GB or RAM in order to have a clean HD capture/display.

I was running with 1GB and was seeing some "lines" (not sure what it is called) when watching fast-moving shows such as an NBA game yesterday. I thought it was because of my low RAM so I upgraded to 4GB but was still seeing the same "lines".

Do I need the additional RAM for a front/back-end machine? I will eventually be adding more front-ends to my system.

Thanks!

Certainly more than 1 GB RAM is necessary. But mostly, HD playback depends on processing horsepower, and/or how much of this processing load can be offloaded to the GPU by using VDPAU or similar. 

There is a wiki page for VDPAU at [http://www.mythtv.org/wiki/VDPAU](http://www.mythtv.org/wiki/VDPAU)

There is also a page to help diagnose HD bottlenecks (the dreaded "prebuffering pauses") at [http://www.mythtv.org/wiki/Troubleshooting:Prebuffering_pause](http://www.mythtv.org/wiki/Troubleshooting:Prebuffering_pause)

---

### Post by tgm4883 on 2010-01-22
Lines isn't very descriptive. My best guess is that you are having vertical sync issues. Can you take a picture?

---

### Post by jquintana on 2010-01-22
Thanks for the replies. My question was not specifically about the issue with the HD playback but more about the RAM.

I will keep the 4GB that I have now.

Thanks for the suggestions about the HD playback -- I will take a look and keep working on getting that fixed.

---

### Post by ian dobson on 2010-01-23
Hi,

Adding extra ram won't help much if your seeing artifacts (in fast moving videos where is looks as if the picture has been chopped into horizontal blocks then put back together but slightly offset from another).

The best thing to do is play with the video playback settings. Make sure you have vdpau enabled, and try various playback profiles (CPU +,CPU++,CPU- High quality).

My frontend has only 1Gb ram and only seems to use about 512Mb no matter what I watch.

Regards
Ian Dobson

---

