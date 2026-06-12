---
title: "Can't install Nvidia proprietary driver for two kernels"
date: 2010-05-26
forum: Multimedia Software
---

### Post by peutch on 2010-05-26
[Sorry this message was posted in Hardware & Laptops errenously.]

Hi everyone,

Sorry to bother you about this. I am stuck on this since my upgrade to 10.04.

I am using the most recent ubuntu kernel (2.6.32-22-generic) for general stuff, and a real time kernel (2.6.31-10-rt) for music recording. Everything was working fine under Karmic.

When I upgraded to 10.04, I had problems with my Nvidia video card, so I uninstalled everying related to Nvidia. And reinstalled the driver using the installer script from the Nvidia website.

I can install the driver for one kernel, but when I boot on the other, it says my X config does not work, and I am back to a low-res no-effect display.

If I then try to reinstall the driver under that kernel, then the first one stops working with the Nvidia driver.

I would be happy to have your advice on how to get Nvidia under both kernel. (If possible some manipulation which I would not have to do everytime I upgrade to a new kernel.)

Thanks a lot for your time!

Peutch

---

### Post by tectp on 2010-05-26
Yes, I'm having the same problem exactly. I was able to use the -rt kernel under karmic but now I can only boot succesfully into the generic version. -rt seems incompatible with the nvidia driver.

---

