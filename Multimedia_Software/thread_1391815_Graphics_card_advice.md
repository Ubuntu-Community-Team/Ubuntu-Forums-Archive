---
title: "Graphics card advice"
date: 2010-01-27
forum: Multimedia Software
---

### Post by judder_man on 2010-01-27
Hi

I'm looking to upgrade my graphics card, but have read horror stories about driver problems, so the main question is ATI or nVidia (those being the main 2) from an ease of install POV?

The reason I'm asking is cos I'm fairly new to Ubuntu, & the installation worked like a dream, so I haven't had to get down & dirty to fix things yet.  (That may change when I get home tonight as I kicked off the upgrade to 9.10 before I left for work this morning, but that's another matter.)

Regards & TIA, Stewart

---

### Post by redzheb on 2010-01-27
I don't have experience with Ati. I'm using nvidia for the past 3 years with Kubuntu. My card now is GeForce 8400 GS and i have no problems (at least no that i'm aware of). With my previous GeForce 6200 i had no problems either. Usually, if you are using Kubuntu (i guess it's the same with Ubuntu as well), when it finds an nvidia card on your hardware, it offers you to use the proprietary drivers for your card. If not, then this link here will help you :)
[http://www.howtoforge.com/enabling-compiz-fusion-on-an-ubuntu-9.10-desktop-nvidia-geforce-fx-5200](http://www.howtoforge.com/enabling-compiz-fusion-on-an-ubuntu-9.10-desktop-nvidia-geforce-fx-5200)
Choose 185 driver, it is working fine. :popcorn:
Cheers

---

### Post by judder_man on 2010-01-27
Many thanks

That link makes things look a lot easier than the ATI sites I have seen, so will look at nVidia first.

At least the upgrade to 9.10 seems to have worked painlessly.

Regards, Stewart

---

### Post by VastOne on 2010-01-27
I build machines with Ubuntu for clients.  I have standardized on the nVidia 9500 GT with 1 gig of memory that sells at 60.00 US at Newegg

Have never had an issue and it is plenty powerful and small footprint

It is hands down the best I could recommend

---

### Post by sports.car.guy on 2010-01-27
nVidia has a more developed proprietary driver at the moment, allowing hardware acceleration, better control of tearing, etc. The AMD proprietary drivers are making advances by leaps and bounds and getting much better. They are now supporting hardware acceleration through their drivers as well, and the interface they are using to access the hardware unlike nVidia is multi GPU capable through plugging in interfaces to it.

nVidia does not have this capability. Also nVidia's hardware accelerated video decoding is a hack in all honesty. It is designed to allow for Linux to access an interface designed for DirectX and DirectX only. nVidia did not design their hardware acceleration to be OS independent. AMD, well ATI with this incarnation of the company being the ones who started the design of their GPU video decoding and acceleration was desinged from the ground up to be OS independent.

AMD / ATI being the primary supplier of GPU's for Apple and the Mac had incentive to, especially when the Mac became a PC. I know people out here who are Apple and Mac fans, there will be a few, are probably going to get mad for that statement, but it is a fact. Jobs has everyone convinced otherwise, but it is a fact. It meant that writing driver code, on the hardware level, was very similar. The same is true for Linux and AMD driver code.

Having this common ground for driver code, along with AMD's OS independent design of their hardware acceleration has led to the drivers for Linux improving by leaps and bounds in a short time. Soon I predict AMD will be working better on nVidia, especially where AMD has become the major on board GPU maker these days.

---

### Post by Schotty on 2010-01-27
> **judder_man said:**
> Hi

I'm looking to upgrade my graphics card, but have read horror stories about driver problems, so the main question is ATI or nVidia (those being the main 2) from an ease of install POV?

The reason I'm asking is cos I'm fairly new to Ubuntu, & the installation worked like a dream, so I haven't had to get down & dirty to fix things yet.  (That may change when I get home tonight as I kicked off the upgrade to 9.10 before I left for work this morning, but that's another matter.)

Regards & TIA, Stewart


SImple answer, 

nVIDIA for best card supported with a closed proprietary driver
Intel for the best open source driver support.

Non gamers generally prefer the Intel GMA's because the driver is clean, and fast (given the nature of the card I cannot disagree).  And Compiz works well on the GMA950's +, so cant complain too much there.  Gaming does suck tho.

Gamers generally have lots of hate to share with AMD/ATI with regards to the laughable Catalyst proprietary driver support.  Do yourself a favor and stick with nVIDIA chipsets if you plan to game, and go Intel for a work/surfage machine.

---

