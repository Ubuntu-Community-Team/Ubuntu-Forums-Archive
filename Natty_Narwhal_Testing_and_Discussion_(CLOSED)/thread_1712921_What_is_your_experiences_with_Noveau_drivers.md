---
title: "What is your experiences with Noveau drivers?"
date: 2011-03-23
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by encefalocardia on 2011-03-23
I just read that the Noveau project is progressing nice and that in "old" cards (Nvidia 8xxx and lower) has better performance if the nveau-firmware package it's also present.

I have a gforce 8600M GT with the restricted drivers and experiencing a lot of crashes using some wine games.

---

### Post by dino99 on 2011-03-23
the best answer is yours :)

install it with synaptic then choose it as "additional driver"

then if you are not satisfied, well choose nvidia-current back

that it, nothing complicated dont you

---

### Post by cascade9 on 2011-03-23
My expereince? More of a pain than tainting my kernel with the closed source drivers.

Still, with nvidia cutting the nv driver, its going to be the only option for newer cards for open source drivers (400 and higher cards will not work with the nv driver). Its enough to drive people to AMD/ATI, at least they support open source drivers, and dont expect the community to make open source drivers for them...with 0 support as well. 

Thanks nvidia. While I'm at it, thanks for optimus as well.  :-#

---

### Post by encefalocardia on 2011-03-23
> **dino99 said:**
> the best answer is yours :)

install it with synaptic then choose it as "additional driver"

then if you are not satisfied, well choose nvidia-current back

that it, nothing complicated dont you

It's really that easy?

> **cascade9 said:**
> My expereince? More of a pain than tainting my kernel with the closed source drivers.

Still, with nvidia cutting the nv driver, its going to be the only option for newer cards for open source drivers (400 and higher cards will not work with the nv driver). Its enough to drive people to AMD/ATI, at least they support open source drivers, and dont expect the community to make open source drivers for them...with 0 support as well. 

Thanks nvidia. While I'm at it, thanks for optimus as well.  :-#

Too bad I cant move to ATI since this is a laptop :/

---

### Post by dino99 on 2011-03-23
[QUOTE=encefalocardia;10592184]It's really that easy?

Sure, forgotten to say that "additionel driver" is found into menu: system-> admin-> additional driver

---

### Post by beew on 2011-03-23
> **dino99 said:**
> the best answer is yours :)

install it with synaptic then choose it as "additional driver"

then if you are not satisfied, well choose nvidia-current back

that it, nothing complicated dont you


What? You use "additional driver" to install the nvidia proprietary driver.  nouveau is already installed and you don't have to do anything. To get 3d acceleration you need to install the package libgl1-mesa-dri-experimental from Synaptic.


@OP

Tried the nouveau driver in 10.10. It is good enough for things like Compiz(with the mesa
package mentioned above) But there are some flickerings and tearing especially for video play back, also of course no vdpau so it uses a lot more cpu cycles for videos. But the worst problem is that the screen would freeze sometimes and requires a hard reboot, though it happens only very rarely.  

I use the nvidia driver as I want to get the best performance out of my hardware. Nouveau is interesting and it deserves support but it is not quite there yet. If you only need basic functions for your graphic card (no hd videos, no gaming..) then Nouveau is fine, otherwise install the proprietary driver.

In Natty nouveau seems to be broken (as is the Nvidia driver), there is a lot more tearing for desktop effects like the Compiz rotating cube than in Maverick and  animations are very sluggish (Cairo dock simply freezes if I click any icon)  This happens in both Unity and the classic desktop.

---

### Post by Quackers on 2011-03-23
I have the same graphics card and am currently using the nvidia drivers. I have tried nouveau and it was much better than previous versions I have tried. However I found it more laggy in performance than closed source. As an example, cairo-dock animations will be considerably slower and will freeze at times - even though the application will still launch.

---

### Post by beew on 2011-03-23
> **Quackers said:**
> I have the same graphics card and am currently using the nvidia drivers. I have tried nouveau and it was much better than previous versions I have tried. However I found it more laggy in performance than closed source. As an example, cairo-dock animations will be considerably slower and will freeze at times - even though the application will still launch.


I think the Cairo-Dock animation problem probably has to do with Natty. In Maverick the Cairo dock animations are just as smooth using nouveau as they are using the Nvidia closed driver (for my system anyway) but in Natty they exhibit exactly the same problems you describe, except the launchers can't even launch the applications most of the time.

---

### Post by Quackers on 2011-03-23
Aha! I see. That could indeed be a possibility. We'll have to wait and see :-)

---

### Post by realzippy on 2011-03-23
My only nouveau experience is when I make a fresh install,means
every 6 month  ;-) and lasts for a few painful minutes running updates before installing NVIDIA driver.I have not bought my nvidia card for not using it,admit I need compiz...good compiz.This is
for my desktop machines....

....being an idiot buying an OPTIMUS laptop,I *cannot* use the nouveau
driver,due to the lack of hybrid graphics support.Since also modern desktop CPUs will have integrated graphics,
where is the future for the nouveau driver
unless the OPTIMUS conspiracy group NVIDIA,Intel,and,yes,Microsoft releases
some code for the nouveau team?
..and even if,the Intel integrated graphics performs better than nouveau/nvidia graphics.
BTW,I am sure that the free ATI driver will offer a hybrid graphics solution sooner,at least for AMD CPUs...
That's it.

---

### Post by cascade9 on 2011-03-23
> **realzippy said:**
> ....being an idiot buying an OPTIMUS laptop,I *cannot* use the nouveau
driver,due to the lack of hybrid graphics support.Since also modern desktop CPUs will have integrated graphics,
where is the future for the nouveau driver
unless the OPTIMUS conspiracy group NVIDIA,Intel,and,yes,Microsoft releases
some code for the nouveau team?
..and even if,the Intel integrated graphics performs better than nouveau/nvidia graphics.
BTW,I am sure that the free ATI driver will offer a hybrid graphics solution sooner,at least for AMD CPUs...
That's it.

Nouveau, intel + open source (I assume), not much difference. 

Optimus probably wont appear on desktop machines. Intel and AMD will have desktops chipsets without onboard video (even if it is in the CPU) for the foreseeable future, the gamer and overclocking sets prefer chipsets without onboard video. 

Optimus (mostly) doesnt even have a direct connection to the video output, which is part of why its such a pain....

IMO nVidia is probably doomed. 

Bumpgate hurt them badly. Thats why apple (and others) dropped nVidia and went to ATI/AMD. 

Intel doesnt want them to be around, and is using its leverage of the CPU/chipset market to push into the video market. Thats how we got poxy intel video anyway, if it wasnt for intels chipset control intel video would still be the joke it was in 1998/1999. i740, bought by nobody, so intel put it into the i810/i815chipsets.  

Intel wont licence nVidia to make iX chipsets, nVidia hasnt released a new AMD chipset for years. They are almost knocked out of the chipset market. 

As for GPUs, Intel is fighting them, AMD/ATI is as well. With the gradual move to 'on CPU GPUs' nVidia will get moved out of the low end, which is the basis for nvidias business in a lot of ways.  

I'd be sorry to see nvidia go, but not as sorry as I was to se matrox go. Yes, yes, I know, matrox is still around in some ways, but who wants a G550 which is an upgraded G450, which is an upgraded G400...from 1999. G800 never came out, parhelia is dead, and matrox is all but gone.

---

### Post by encefalocardia on 2011-03-23
For those saying that the drivers are broken on natty, remember that as in any alpha and beta OS the debugger is running so slow downs everything.

---

### Post by Simian Man on 2011-03-23
> **encefalocardia said:**
> I have a gforce 8600M GT with the restricted drivers and experiencing a lot of crashes using some wine games.

Those are almost certainly due to problems with wine and not yuor graphics drivers.  Nouevau is usable, and open source, but the performance of 3D applications is still nowehere near that of the official Nvidia drivers.  Nouveau isn't going to help you.

---

