---
title: "CPU vs GPU, can someone help me understand?"
date: 2008-11-01
forum: Multimedia Software
---

### Post by Phases on 2008-11-01
Hey guys. 

I'm just trying to understand how this works. I have two video cards in my box, one monitor on each, defined in xorg.conf obviously, etc. So, I thouht this meant each one would do it's own thing. But.. well, an example.

Ok, I open 2 Firefox session. Put one on each monitor, go to youtube and let sit idle. My CPU runs at like 5 or 10%. If I start playing a youtube video on one of the monitors, my CPU usage jumps up to around 25%. If I start playing a video on the other monitor, not only does the usage jump up to more like 45%, but both videos become choppy. 

Now I know my system isn't the greatest anymore, you know, amd64 x2 4800+ Toledo.. and two 256mb 6800GS video cards, but shouldn't it be able to handle that? 

I thought the workload was to be put on the video cards, so why is this what I'm seeing? Also I saw a video on youtube where a guy did a comparison rendering of something on CPU then GPU, which helped fuel this post. Is there something I'm missing in my xorg.conf maybe? Or is this normal? 

(But, I think I've tried most every option/module out there tryin' to fix this tearing problem before I noticed this)

Lastly, is there something I can use to test my performance, see how each GPU does or something? glxgears I've used but that doesn't provide much detail.

Anyway, thanks for any help understanding..

---

### Post by tootlet on 2008-11-01
Hi Phaz,
What kind of broadband are you using? Maybe this isn't a problem with your CPU/GPU but you just don't have the bandwidth to run 2 streaming videos simultaneously. Just a thought.
T

---

### Post by cb951303 on 2008-11-01
is hardware acceleration on for flash?
right click a youtube video > settings > enable hardware acceleration

EDIT: Also you may try it with 2 non-flash videos and see if it has something to do with flash plugin?

---

### Post by Phases on 2008-11-01
Hey guys, thanks for the replies! 

> **tootlet said:**
> Hi Phaz,
What kind of broadband are you using? Maybe this isn't a problem with your CPU/GPU but you just don't have the bandwidth to run 2 streaming videos simultaneously. Just a thought.
T

Comcast cable. I'm not exactly sure the numbers, it's a step up from the minimum speed they offer.

> **cb951303 said:**
> is hardware acceleration on for flash?
right click a youtube video > settings > enable hardware acceleration

EDIT: Also you may try it with 2 non-flash videos and see if it has something to do with flash plugin?

Yeah, the box is checked for hardware acceleration.

When I try it with two downloaded high resolution diggnation videos, it eats through my CPU power in htop, by they play equally as smooth as if I just watched it once. 

So, on the one hand - sounds like it may be a problem with either a) flash, or b) streaming from the intertubes, but either way... still brings me back to my original question. When I do that it rips through my CPU power - shouldn't it be using each cards GPU?

Appreciate ya'll takin' the time to work with me.

---

### Post by Phases on 2008-11-02
I'm just trying to understand. It seems when I do graphically intensive stuff, like render stuff inside my cube or something, it tears into my CPU. 

Isn't that what the GPU is for?

---

### Post by cb951303 on 2008-11-02
there may be a SLI problem with new linux drivers? look for bug reports. also try using the old drivers. I think both 173 and 177 are in the repo

---

### Post by Phases on 2008-11-02
I'm on 177, and no SLI. Just 2 cards and 2 monitors. 

Thanks for the reply :)

---

### Post by cb951303 on 2008-11-02
> **Phases said:**
> I'm on 177, and no SLI. Just 2 cards and 2 monitors. 

Thanks for the reply :)

173 might help anyway. sometimes newer drivers have regressions

---

### Post by Phases on 2008-11-02
Ok I'm wholeheartedly confused here. In the repo's it shows 173, and it's green for installed, and says my installed version is 173.

But I have 177 sitting right here, NVIDIA-Linux-x86-177.80-pkg1.run  from their website that I'm 100% certain I installed through CLI, and even had it compile it's own something or another. (twice)
 
...yet, synaptic says I have 173 installed.

---

### Post by cb951303 on 2008-11-02
That's normal. Synaptic only works with APT. It would be better to remove first 173 though and then install 177 from CLI. BTW in 8.10 there is a 177 package in repos. You should use it instead of installing it with *.run

---

### Post by Phases on 2008-11-02
As soon as 8.10 gets support for Xinerama/xserver-xgl setup I have going I will switch to it... and 64-bit. I'm excited to do that but until that issue is resolved I need to hang around on 8.04 a bit :)

---

