---
title: "intel 915gm which driver?"
date: 2006-09-26
forum: Multimedia &amp; Video
---

### Post by maddocks on 2006-09-26
Hello,
        I have a laptop which has a intel 915gm video card. Im runnen a 2.6 kernel compiled for 686. My question is which 915 driver should I use. Resources have been conflicting. For instance are the drivers from intellinuxgraphics.org , intel.com, and [http://dri.freedesktop.org/snapshots/](http://dri.freedesktop.org/snapshots/) all the same driver? Many forum's have said yes and no. I know I compiled the ones from dri.freedesktop.org and they worked fine (i810 and i915) but I had terrible performance (glxgears runs at 500fps with 128mb of ram allocated to video). Both the ones from intel.com and intellinuxgraphics.org dont compile correctly and both claim to only work with 2.4 kernel. I have read many posts of people who claim to have gone from 500fps in glxgears to 1500fps using the binary intel driver. This is what I know the dri.freedesktop.org compiles fine and creates i810_drv.so and i915_dri.so which work fine and it uses mesa's libGL.so. My ati cards have there own libGL.so bundled with the driver. So im assuming I would recieve either better performance or more hardware accelerated graphics with a libGL.so specifically written for my driver is this so? One of the other driver packages I believe fron intel.com comes with it own libGL.so file which is considerably larger in size then mesa's. I tried replacing mesa's with intels. I rebooted and had no more Direct rendering. Since the libGL.so from intel.com didnt work with the driver from dri.freedesktop.org I assume these drivers are different. Also in the readme to intel.com's driver it lists intel_drv to be the binary driver required to gain accelerated 3d graphics and direct rendering. Well when I compile intellinuxgraphics.com drivers (both i810 and i915) it creates no intel_drv.so file but does create (While compiling it shows these files but cannot be found when compiling is finished) i915_3d.so and another that I cant remember but it wasnt i915_dri.so. So as far as I can tell ( and hope to have clarification)
1. all three websites have different drivers and each set uses different driver names.
2. The intel.com and intellinuxgraphics.org are originally written for 2.4 kernels but some have claimed success with 2.6 kernels.
3. Intel.com has a non open source binary driver which increases performance adds more hardware accelerated 3d, and includes its own libGL.so file. But "might" only work on a 2.4 kernel?

In the end Which driver gives the best performance. Which driver names does that driver bundle use. Does that driver support 2.6 kernels. Does using mesa's libGL.so compared to your drivers libGL.so make a difference? 

I know I have been long winded and I apologize Im just so confused about which path I should take to get the best performance or at least the most hardware accelerated option for I use compiz/XGL. I know my card supports hardware accelerated options that my processor is doing now slowing down the whole shubang. Any info at all regaurding this would be great. THANK YOU!!! my email is ben at buckys.tv or bmaddocks at wildmoo.net

---

### Post by jrjazzman on 2006-10-13
So, anyone have any info here?  I have a 915 using the "i810" driver.  2d speed makes my computer look like a 386.  Is the Intel binary driver any better?

---

### Post by rlozano on 2006-10-13
well, actually this is the same saga i have now... :) my notebook is using intel graphics card and it widescreen...

i'll keep on searching, and if there's anything that i think will be able to help, i will post it here...

---

### Post by almahtar on 2006-10-20
Ditto, rlozano.

---

### Post by tflovik on 2006-10-20
i Have an Dell laptop(inspiron 6000) with gm915 graphics.
Ubuntu configures the driver automatically and i have an fps around 1100.
I have done nothing to improve any settings and it works well with 3d.

---

### Post by jrjazzman on 2006-10-20
was glxgears full screen, and what is your screen res?

> **tflovik said:**
> i Have an Dell laptop(inspiron 6000) with gm915 graphics.
Ubuntu configures the driver automatically and i have an fps around 1100.
I have done nothing to improve any settings and it works well with 3d.

---

### Post by almahtar on 2006-10-25
I've found that the i810 driver in the repositories is superior to every alternative I've tried.  Anyone else have results?

---

### Post by zgornel on 2006-10-27
i915 3D performance compaired to Windows XP is very very poor.

---

