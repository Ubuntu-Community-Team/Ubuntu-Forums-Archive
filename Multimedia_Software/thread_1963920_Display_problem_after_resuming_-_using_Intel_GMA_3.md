---
title: "Display problem after resuming - using Intel GMA 3600"
date: 2012-04-23
forum: Multimedia Software
---

### Post by yfaney on 2012-04-23
Hello, I am using ASUS eeePC X101CH laptop and I installed the Ubuntu 11.10.

But it couldn't apply the Intel GMA 3600 display driver, so I compiled the 3.3.2 Kernel with the driver.

So now it works, but I've got another problem.

My display doesn't work as the following attached file after resuming the PC from sleep mode.

Before compiling the resuming process was OK.

So in summary,

Before compiling : Display Driver (No : VESA) / Resuming after sleep mode (O)
After compiling : Display driver (Y : GMA 3600) / Resuming after sleep mode (X)


If anyone knows or can guess what is the cause, please help me.

Thanks,

Best regards,
Younghwan Jang

PS : I copied this thread from Hardware & Laptops Category

---

### Post by shokocham on 2012-07-24
Hi!
I think I found  a way to suspend and resume properly. I also have an x101ch netbook (with gma 3600), but am using debian.

At first, I compiled kernel 3.3.2 with the gma 3600 driver, and couldn't resume from suspend. The screen would stay completely black, unlike your attached photo, which looks similar to static noise.

But with kernel 3.4.4 (and gma 3600 driver), I could properly suspend and resume by issuing the following command as root:
```
pm-suspend --quirk-vbestate-restore
```I suggest you compile kernel 3.4.4.

Suspending regularly results in rectangles of colors filling my screen.

Let me know if that helps. If this works for anyone with a different computer that uses gma 3600, please post so others know.

---

