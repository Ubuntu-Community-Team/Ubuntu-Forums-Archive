---
title: "[SOLVED] ATI Vs. NVIDIA Vs. Intel Graphics"
date: 2008-07-30
forum: Multimedia Software
---

### Post by Nxion on 2008-07-30
What is your thoughts on the three above brands. What brand would you choose and why. Also what struggles have you had configuring ATI, Nvidia or Intel video cards.

And can you give me a recommendation on what I should look buy?

What I do:

This will be a laptop
Multimedia (Pictures and Video, play DVDs)
No gaming
I use the terminal more than the GUI

can't think of anything else at the moment. if you all need more info let me know!! :)

Thanks,
Nx

---

### Post by jeremy1138 on 2008-07-30
Nvidia...  I have an ATI and it doesn't work the best.  I don't really know about Intel video cards but my wife has and Nvidia and it works great without any messing around.  I'm sure others will agree Nvidia is the way to go.

---

### Post by tuxxy on 2008-07-30
nVidia, definitely their drivers are much better,  nVidia will give you flawless effects and good 3D graphics.

I run an ATI card aswell in another system I have issues on that system with 3D and some effects in compiz.

---

### Post by Melcar on 2008-07-30
For the uses you specified I would go for an Intel chip.  Stability wise, it will trump both ATI and nvidia.  It will probably be cheaper too.

---

### Post by rossjman1 on 2008-07-30
Nvidia has always been good when it comes to Linux support. ATI has been making great strides in recent years. Intel cards are usually always supported (but they suck if you're looking to run compiz). All in all, it really depends on which card you get. I've had an ATI card run flawless with little configuration while I have had Nvidia cards that are not so flawless, and vice versa. Just do a little research before you decide.

---

### Post by tamoneya on 2008-07-30
i vote intel.  Yes integrated cards dont have the same power but intel is definately the best when it comes to drivers.  Most linux users are heavy gamers anyways so its okay to have less power then a discrete card.

Can anyone say price?

Nvidia fans: read this article [http://www.phoronix.com/scan.php?page=article&item=nvidia_173_14_12&num=1](http://www.phoronix.com/scan.php?page=article&item=nvidia_173_14_12&num=1)

---

### Post by sloggerkhan on 2008-07-30
If you need graphics power I think AMD/Ati is the way to go. nvidia is slacking, fglrx will (IMO) give you better video playback, and the fglrx driver improves every month, sometimes very significantly.

Intel works great, but will be underpowered if you do gaming and heavy 3-D.

nVidia works decent, but I think their video playback isn't the greatest, and the driver doesn't seem to improve much over time. Plus with ATI, you might have an option of open source driver that even does 3-D. No such luck with nvidia.

So basically, don't use the gpu so much, go Intel, do need it, try ATI.

---

### Post by Melcar on 2008-07-30
> **sloggerkhan said:**
> If you need graphics power I think AMD/Ati is the way to go. nvidia is slacking, fglrx will (IMO) give you better video playback, and the fglrx driver improves every month, sometimes very significantly.

Intel works great, but will be underpowered if you do gaming and heavy 3-D.

nVidia works decent, but I think their video playback isn't the greatest, and the driver doesn't seem to improve much over time. Plus with ATI, you might have an option of open source driver that even does 3-D. No such luck with nvidia.

So basically, don't use the gpu so much, go Intel, do need it, try ATI.



Definitely.  Right now, if you want a "gaming" card that works out of the box (literally) and can run most open source games and Compiz (and don't mind using an older card) ATI is the best choice.  Now, once Gallium comes out ATI will be the only real choice if you want a powerful 3D experience out-of-the-box... that is until Larrabee pops up (and if Intel keeps their drivers open).

---

### Post by tuxxy on 2008-07-30
ATI drivers dont even run 3D graphics properly....

---

### Post by farlander762 on 2008-07-30
Nvidia works for me on two computers.  I don't know much about ATI and I have never liked Intel chipsets (graphics or otherwise).  I love Intel processors but every confuser I have ever run with an Intel chipset was flaky.  

Right now I am running two computers with Nvidia graphics.  One is an old GeForce 4 128MB running two monitors.  The other is a GeForce FX 5200.  The 5200 is 3D and really looks good.  The older GeForce 4 has just been a reliable workhorse for 5 years now.

I am about to make a post on how I got the cards to do what I wanted.

---

### Post by djxcon on 2008-07-30
If heavy 3D gaming is not important for the laptop and you just want a nice and slick desktop experience, my vote is definitely Intel.  Runner up would be ATI with the open source driver.  When asking a question like this, you have to expect the answers to be all over the map.  Good luck!

---

### Post by tuxxy on 2008-07-30
Trust me if you want a nice and slick desktop experience with flawless compiz effects you should go for nVidia.  I run both types of card with Ubuntu 8.04 and the ATI drivers are poor in comparison.

---

### Post by jeremy1138 on 2008-07-30
> **tuxxy said:**
> Trust me if you want a nice and slick desktop experience with flawless compiz effects you should go for nVidia.  I run both types of card with Ubuntu 8.04 and the ATI drivers are poor in comparison.

I agree.  My ATI card won't run any 3d games and whenever anything 3d is displayed, it maxes out the processor.  As I said before, you should go with Nvidia.

---

### Post by Charlie708 on 2008-07-31
Intel's integrated chips are becoming more powerful, and Intel has great support.  Unless you need something more powerful, I would stick with an Intel IGP.

---

### Post by sloggerkhan on 2008-07-31
> **tuxxy said:**
> Trust me if you want a nice and slick desktop experience with flawless compiz effects you should go for nVidia.  I run both types of card with Ubuntu 8.04 and the ATI drivers are poor in comparison.

What driver do you use?

---

### Post by steefjeqv on 2008-08-01
Hi,

Well, for the use you've specified in your original post I'd say :

First choice would be intel :
[http://www.phoronix.com/scan.php?page=article&item=intel_x4500hd&num=1]("http://www.phoronix.com/scan.php?page=article&item=intel_x4500hd&num=1")

Second choice : AMD. They've made great efforts for the open-source community in the last year. No open-source 3D for the moment, but it should be available in the next 6 months or so. Be very careful using their closed-source "fglrx" driver, it only meant trouble for me.

Third choice : Nvidia. They're not so good in "open-source", but they do have their closed sourced driver, which works quite good. Video playback isn't that good.

I have one Nvidia graphics PC (closed source driver) and one ATI/AMD graphics PC (open source driver). The largest difference driver-wise (in my opinion) :
The ati driver has improved over the last year whereas the nvidia driver hasn't changed that much (video playback is not good and nothing has been done about it so far).

Greetings,
Steven

---

### Post by Nxion on 2008-08-13
Thanks everyone who replied. I think Ill be getting an intel for my next laptop. Or I might try out the ATI. Its not set in stone yet :)

---

