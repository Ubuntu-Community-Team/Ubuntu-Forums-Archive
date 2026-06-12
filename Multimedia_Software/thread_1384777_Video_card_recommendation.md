---
title: "Video card recommendation"
date: 2010-01-18
forum: Multimedia Software
---

### Post by CompSciSTL on 2010-01-18
Hello,

I would like to undertake the task of building a HTPC with Mythbuntu (I would prefer to use the 64-bit version unless there is compelling reason otherwise), and I was wondering which Nvidia based card would be best for the job?

I am hoping to find a card that is either passively cooled or has a really quiet fan, a card with a HDMI port, and something  with enough horsepower to play Blu-ray (maybe?) on a 40" LCD TV.

The only definitive components I have on the system so far is that it'll be an Intel Q9450 processor with 4GB of RAM.  A Velociraptor will be used on the front-end.

Thanks in advance for the advice!  :popcorn:

---

### Post by sports.car.guy on 2010-01-19
A lot of people will tell you NVidia and I would agree to some extent, but, and there is always a but. AMD GPU support with their proprietary drivers has come a long way.

_**Buying NVidia:**_

You can take advantage of well developed hardware offloading with their proprietary drivers. VDAPU is the name of this technology they have developed with the open source community. From what I have read and heard from some people who use these GPU's it works very well and creates great quality picture reproduction. Their GPU's have great vertical syncing to handle and put a stop to tearing too.

Higher pricing is an issue. This is one downfall to NVidia and why I like ATI/AMD GPU's. Their GPU's used to be a lot lower cost wise for what you get. NVidia did in my opinion a name standards change for their GPU's to be shady. Some of their supposed newer video cards are just repackaged old ones, nothing more, and you pay more because of the name change. Also because of this change to naming their hardware you can have two totally different GPU's technology wise sharing the same tier of badging.

You buy NVidia you really need to research the cards individually and dig into them deep. You could end up paying top dollar and find the next one up or even down on the model ladder has better stats, so much so you will want to cry.

_**Buying AMD:**_

Buying an AMD GPU you need to make sure you are buying one that will have support through their proprietary drivers for some time. The reason for my saying this is because they are now just having their own hardware decoding become truly available to Linux, which from my use of it so far in MPlayer looks beyond promising. It is only a matter of time before a patch to MythTV or a new version of it arrives supporting the interface it uses. It will allow for nearly all GPU's to have an interface layer with the Linux graphics library that is standard. This is one thing to wait for but not a hold your breath situation to have hardware decoding of video by the GPU.

The cost for AMD based video cards is very reasonable, especially for what you are getting on the note of capabilities and performance. I purchased a Saphire HD4670 for this system and I love it.

The only downfall I have encountered, which no matter what people say about it not getting any better, has improved dramatically. This is the issue with vertical syncing. They are working on this problem and have enacted some fixes for them that can be enabled in xorg.conf and do the trick for the most part. They are also dependent on the version of catalyst and how much they help for some reason.

Like I was using CCC 9.10 and it was a big step up from 9.9, but 9.8 was better then 9.9 performance wise. When it comes to my seeing tearing happening, it is on occasion now at the bottom of the screen when watching TV or a movie. I will say this honestly too, that where it happens I don't even notice it unless I am obsessively looking for it and then it is there not too often.

If you can deal with an occasional tear that is usually not where it is noticeable, not having hardware decoding in applications like MythTV yet, I would say buy AMD.

AMD is worth some of the slight problems when you pay $30 for a card from them and the equivalent performance wise from NVidia is almost triple the cost.

I bought this HD 4670 well over a year ago on sale at NewEgg for $60 and change with a rebate to boot. I have no complaints and actually really like the card. I have owned both of the big two GPU maker's cards too. This is not some biased AMD camp opinion. If we were talking CPU's, then it would be another story. I am very biased about processors and am an AMD man on that note..lol

---

