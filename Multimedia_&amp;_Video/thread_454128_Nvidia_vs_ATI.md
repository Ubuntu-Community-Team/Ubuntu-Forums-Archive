---
title: "Nvidia vs ATI"
date: 2007-05-25
forum: Multimedia &amp; Video
---

### Post by robert2003 on 2007-05-25
So I have been reading a lot about Nvidia graphics cards working better with Linux than ATI cards. Is this true, or a bunch of hype? I want to know, if I buy a new PC with an Nvidia graphics card, will Ubuntu (and Beryl/Compiz) work much more easily?

Thanks!

---

### Post by Darkriser on 2007-05-25
From my own experience with both brands - I strongly recommend nVidia. Now I have 6600 series, installed drivers using [this thread]("http://ubuntuforums.org/showthread.php?t=263851")  (STEP 2 -> Option 2) and everything went smooth and easily. 3D, beryl, everything...

Marcel

---

### Post by eye208 on 2007-05-25
> **robert2003 said:**
> So I have been reading a lot about Nvidia graphics cards working better with Linux than ATI cards. Is this true, or a bunch of hype?
It was true some time ago, now it is hype.

---

### Post by lundish on 2007-05-25
still ati sucks :) at least for me. no pivot, no proper working beryl. 

go for nvidia

---

### Post by eye208 on 2007-05-25
> **lundish said:**
> no proper working beryl.
What does that mean, no proper working Beryl?

---

### Post by viciouslime on 2007-05-25
> **eye208 said:**
> What does that mean, no proper working Beryl?

It means the ATI drivers aren't anywhere near as good as the nvidia ones. Basically, you have to mess around setting up an XGL layer and this causes lots of problems if you want to run 3dapplications/games at the same time as using beryl/compiz. I would definitely go with nvidia. If you read around the forums the majority of people having problems with beryl/compiz are ATI users.

Of course if you're not bothered about beryl/compiz, then this might not be an issue for you. Also, it has recently been announced that ATI will open-source their drivers, they haven't given a time-scale though.

In short: go for nvidia, much better linux support all-round at the moment.

---

### Post by eye208 on 2007-05-25
> **viciouslime said:**
> and this causes lots of problems if you want to run 3dapplications/games at the same time as using beryl/compiz.
Beryl/Compiz fcks up 3D apps and games anyway, no matter what driver or server you use. That's why people recommend to switch it off or launch a separate instance of X for running those apps. If you want Beryl/Compiz on ATI, there's no need to install binary drivers since the OSS radeon driver supports AIGLX out of the box. Either way you have to decide what you want as there is no one-size-fits-all approach yet.

> I would definitely go with nvidia. If you read around the forums the majority of people having problems with beryl/compiz are ATI users.
If you include old threads then this is true. However, if you look at *current* threads you see more people having issues with Nvidia's driver. As soon as AMD makes the ATI driver open source, ATI will become the no. 1 choice on Linux. They are pressured to do so since Dell has started offering ATI-powered laptops with Ubuntu.

---

### Post by TheMono on 2007-05-25
Where do I start? AMD are not comitted to opening the ATI driver. The Dell laptops with Ubuntu do not have ATI graphics.The OSS Radeon driver does not support AIGLX on all cards by any means, merely the R3XX and before.

Having said that, ATI aren't as bad as they are made out to be on the forums if you get an older card, but for the new ones they are virtually a lost cause.

---

### Post by eye208 on 2007-05-25
> **TheMono said:**
> AMD are not comitted to opening the ATI driver.
[http://enterpriselinuxlog.blogs.techtarget.com/2007/05/09/amd-will-deliver-open-graphics-drivers/](http://enterpriselinuxlog.blogs.techtarget.com/2007/05/09/amd-will-deliver-open-graphics-drivers/)

---

### Post by joe.turion64x2 on 2007-06-30
> **eye208 said:**
> Beryl/Compiz fcks up 3D apps and games anyway, no matter what driver or server you use. That's why people recommend to switch it off or launch a separate instance of X for running those apps. If you want Beryl/Compiz on ATI, there's no need to install binary drivers since the OSS radeon driver supports AIGLX out of the box. Either way you have to decide what you want as there is no one-size-fits-all approach yet.


If you include old threads then this is true. However, if you look at *current* threads you see more people having issues with Nvidia's driver. As soon as AMD makes the ATI driver open source, ATI will become the no. 1 choice on Linux. They are pressured to do so since Dell has started offering ATI-powered laptops with Ubuntu.
At least my ATI Radeon Xpress 1100 does not support AIXGL with the OSS radeon driver out of the box, in fact even with the fglrx drivers installed.

I am out of luck if everyone else's ATI card does!

---

### Post by Sonuken on 2007-07-01
I have ATi X1600 Pro working flawlessly with compiz fusion :) but still, nvidia is better i  guess.

---

