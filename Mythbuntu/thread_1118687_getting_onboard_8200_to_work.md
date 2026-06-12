---
title: "getting onboard 8200 to work"
date: 2009-04-07
forum: Mythbuntu
---

### Post by stevecartermo on 2009-04-07
Hi

I am setting up a new mythbuntu with the 9.04 beta, I see the mythbuntu boot screen but after X starts it seems to tear the display and it is unusable, (can't see anything).

I installed a PCI video card and mythbuntu booted fine and allowed me to install the system.

I downloaded the latest NVIDIA drivers to the desktop and I was thinking of booting to a terminal and installing them, but it seems as though most people think the best way to install them is through the restricted drivers manager.

Any suggestions for getting my onboard 8200 going ?

the board is an ECS GF8200A, cpu is an AMD X2 4850 and I am attempting to install 9.04 beta 32 bit

Thanks

Steve

---

### Post by SigmaSanti on 2009-04-08
Hey Steve,

I have an XFX 8200 board with Amd 64 5400 x2, This board has the nvidia 8200 integrated graphics chip and has been an endless source of problems for me. I often have unusual crashes with certain windows and menus and have yet to have a perfect installation of ubuntu using it. 

I have used with varying amounts of sucess all the nvidia drivers from 173 to the 185 beta - none of them have worked perfectly. Howevery Nvidia has improved their drivers a lot with 180.44

 As to why it is not working for you, That could be from running 9.04 - its still being worked on - and when I updated my computer yesterday compiz crashed my system on startup.

I recommend that you try using the vesa driver when you boot up ( I think you can do that if you select safe graphics mode ) - that worked for me after a failed graphics driver or install the latest stable driver - 180.44 from Nvidia. You can also install ubuntu 8.04 or 8.10 and see if those work.(They work okay for me)

Hope this helps, but honestly I think their is little that you or I can really do - except by buying a real graphics card next time.(I plan on doing that ;) )

P.S. If you give up on the 8200, see if their is a way of turning it off in the bios so it does not keep on sucking up power.

---

### Post by stevecartermo on 2009-04-08
Thanks for the REALITY CHECK. Unfortunately this board exhibits the same problem with 7.1 8.04 and 8.1. Again I see the Mythbuntu screen ok, but when it looks like X should be starting the screen is torn and it looks like I am getting 4 similiar images at the top of the screen. I can't recognize the images so I am not sure how far in the boot process it gets. The machine has the same behaviour in safe graphics mode. So right now I have an old PCI graphic card and it is working ok, but this is a new backend so I was looking forward to setting it up and leaving it for a year.

Thanks again for your input.

---

