---
title: "how do I get jack to run nicely? latencty and xruns too high"
date: 2010-06-07
forum: Multimedia Software
---

### Post by joels on 2010-06-07
Hi,
I'm trying to get jack to run with soopelooper. I can get them both to work, but the latency is too big (40msec or thereabouts). The frames/period is 1024. I'm running jack as realtime, and with the memlock as unlimited. The 
My computer is a toshiba, with a dual core 3.2ghz processor and 4 gb of ddr2 ram.
If I drop the frames/period down however (to 512 or lower), I get lots of xruns in the jack window. Something I assume is not good. 
Can anyone please help?

---

### Post by Breambutt on 2010-06-07
Which version of Ubuntu are you using? Ubuntu Studio comes with a realtime kernel (although sadly enough not Lucid - yet) which has a lot to do with low latency operation. Of course it depends on your hardware as well, but I assume this has been tested with reasonable latencies in Windows or somesuch.

Sample rate also affects the latency and if I'm not mistaken, your user needs to be a part of the Audio group in order to use realtime. I might be mistaken though, it's been a while since I've actually had to bother looking into things - it's so streamlined in these multimedia distros that you barely have to tweak anything.

Oh yeah, you might also want to try upping periods/buffer by one. There's just so much you can (and should) try. Trial and error like the monkeys we are.

Try searching for realtime kernel (possibly in the Ubuntu Studio subsection) on these forums, I think there's a couple of pre-packaged realtime kernels floating around in case you don't feel like compiling one yourself.

---

### Post by joels on 2010-06-07
I am using Ubuntu 10.04 (not "Studio" version). I am part of the audio group, and have ticked "realtime" in Jack. I'm not, however, running a realtime kernel (I don't think).
Is a realtime kernel a better option? For everyday stuff, like email, photos, etc... too? Also, is it better to download a pre-packaged one (which one should I get?) or compile one myself (and is that really hard?).
Thanks (lots of questions, I know, sorry...)

---

### Post by Breambutt on 2010-06-07
Realtime kernel is like any other kernel except for the lower latency part and Ubuntu Studio is basically Ubuntu which is preconfigured for audiovideo use for your convenience. Anyone who has MIDI keyboards or other similar needs for low latency operation should probably use a realtime kernel.

I've been using Ubuntu Studio as a hybrid setup for years; multimedia production machine, gaming and everyday nerd stuff. For different kind of hardcore audio nerding there's 64studio and pals, but I'd recommend giving Ubuntu Studio a go as an all-around machine for any musician since fiddling with kernels without much experience isn't always fun or a cakewalk in the park, and that way you get all the realtime kernel updates automatically. 

Well, that's implying you should wipe your entire system, which wasn't my intention. See here for more info on the rt kernels in Lucid, at the moment we're in the same boat with regular buntu and studiobuntu: [http://ubuntuforums.org/showthread.php?t=1470264](http://ubuntuforums.org/showthread.php?t=1470264)

---

