---
title: "Radeon X1600"
date: 2009-10-11
forum: Multimedia Software
---

### Post by intranick on 2009-10-11
Well its been a couple years since i had a graphical linux machine, so im kinda rusty.

I recently got my world of warcraft account hacked because of windows' inadequecies as an operating system and I decided to install linux.  within an hour i had downloaded ubuntu, slapped it on my hard drive, and proceeded to try to install the video drivers for my radeon x1600

when I try to install it i get 
>  
Error: ./default_policy.sh does not support version
default:v2:i686:lib::none:2.6.28-15-generic; make sure that the version is being
correctly set by --iscurrentdistro


I think its telling me my kernel is the wrong version but im not sure.  anyone else have experience with this problem? how can i solve it?

---

### Post by mcduck on 2009-10-11
The only drivers working for X1600 are the opensource drivers that Ubuntu uses by default.

Ati/AMD dropped all support for older GPUs some driver versions ago.

The bright side is that the opensource drivers have improved a lot, and give better battery life and less problems than the fglrx drivers ever did. And the 3D performance is quickly getting better as well.

---

### Post by intranick on 2009-10-11
how would i go about updating them?  just watching the screensaver I get the feeling that the graphics arnt that accelerated.  

All i want this computer to do is play world of warcraft..

---

### Post by DEagleson on 2009-10-11
My gpu is a ATI Mobility Radeon X1600 256mb and my card struggles even with the simplest OpenGL 3D games.
It does do 2D really good.

Maybe we would see a major preformance boost once Gallium3D gets released, but for now a windows dual boot or a old distro where AMDs propetary ATI driver still supported legacy cards to get useful 3D acceleration.
I dont recommend the ATI linux drivers with old distro solution.

---

### Post by morrie on 2009-10-13
Are you sure you've got the right info, McDuck?

What about the info here:
[http://www.linux-magazine.com/Online/News/Proprietary-Driver-for-Ubuntu-9.04-Fglrx-for-X-Server-1.6](http://www.linux-magazine.com/Online/News/Proprietary-Driver-for-Ubuntu-9.04-Fglrx-for-X-Server-1.6)

and here:
[http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.9&lang=English](http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.9&lang=English)

I mean it says that they aren't supporting it, but I have major problems with my 9.04 Install / Radeon X1650 so I am willing to try anything.. (I'll let you know...)


I got past that error by doing this:
/ati-driver-installer-9-3-x86.x86_64.run --buildpkg Ubuntu/jaunty

---

### Post by morrie on 2009-10-13
... The install still failed in the end...

alas

---

### Post by mcduck on 2009-10-13
> **morrie said:**
> Are you sure you've got the right info, McDuck?

What about the info here:
[http://www.linux-magazine.com/Online/News/Proprietary-Driver-for-Ubuntu-9.04-Fglrx-for-X-Server-1.6](http://www.linux-magazine.com/Online/News/Proprietary-Driver-for-Ubuntu-9.04-Fglrx-for-X-Server-1.6)

and here:
[http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.9&lang=English](http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.9&lang=English)

I mean it says that they aren't supporting it, but I have major problems with my 9.04 Install / Radeon X1650 so I am willing to try anything.. (I'll let you know...)


I got past that error by doing this:
/ati-driver-installer-9-3-x86.x86_64.run --buildpkg Ubuntu/jaunty

Like the article you posted says:
> 
The downside is that the newest generation of the driver doesn't support any of the "older" ATI chipsets, which at this point include the R300 through R500 chipsets.


And the other page lists all cards from Radeon 9500 to Radeon X2100  as "legacy".

So yes, I am sure, and these pages only confirm what I said.

---

### Post by lenux- on 2009-10-13
I beilieve AMD/ATI is doing same thing with linux as with windows.

I think they stated they would do less frequent legacy drivers, which makes sense since it is unlikely people with older cards are on the update driver every month train anyway.

example: windows world they skipped drivers between 9.3 and 9.8 so they are just not updintg it that often anymore.

---

### Post by mcduck on 2009-10-13
> **lenux- said:**
> I beilieve AMD/ATI is doing same thing with linux as with windows.

I think they stated they would do less frequent legacy drivers, which makes sense since it is unlikely people with older cards are on the update driver every month train anyway.

example: windows world they skipped drivers between 9.3 and 9.8 so they are just not updintg it that often anymore.

In that case it still remains to be seen how long interval the "not so often" is going to be, since they haven't provided a single driver that would support these "legacy" chips since they moved them to legacy status. And they haven't said anything about providing any drivers in the future either. Even those articles posted above only mention that Ati/AMD might provide windows XP/Vista drivers for critical bug fixes, and in the very same sentence that they will not provide any more Linux drivers.

Actually it seems quite a lot like they have decided that since they have provided the required information to the opensource driver project they don't have to bother with supporting their own chips any more..

---

### Post by morrie on 2009-10-13
The article is saying that the "legacy products" are no longer supported, and states that the listed products are compatible with 9.3 (and NOT_ future_ Catalyst releases)

> All future ATI Catalyst™ releases made available past the ATI Catalyst™ 9.3 release will not include support for the legacy products listed above or any of the features associated with those legacy products.

So, we should be able to get 9.3 working (if it's even worth it; I know I was using 9.8 on Windows).

Or is it probably a better use of our time going to the store and getting the $30 Linux compatible special (which is probably GEForce7600, by now at least)?

Anyone?

---

### Post by mcduck on 2009-10-13
> **morrie said:**
> The article is saying that the "legacy products" are no longer supported, and states that the listed products are compatible with 9.3 (and NOT_ future_ Catalyst releases)



So, we should be able to get 9.3 working (if it's even worth it; I know I was using 9.8 on Windows).

Or is it probably a better use of our time going to the store and getting the $30 Linux compatible special (which is probably GEForce7600, by now at least)?

Anyone?

Well, 9.3 only works with older versions of Xorg and Linux kernel than what current Ubuntu versions are using. And downgrading those is not an easy thing to do, if really even possible without breaking most of the system.

So in the end you are only able to use old version of the driver and would have to run it on old Ubuntu version (8.10 or older). If you want to run up-to-date system your only option is to use the opensource drivers.

---

### Post by mcorbeil on 2009-12-16
Thanks McDuck! You pretty much made it as clear as crystal what the situation is with the AMD/ATI drivers. In the future I won't be buying anymore of their cards for fear of them doing the same thing with their current "non-legacy" cards. I'm positive this has been a real issue in the adoption of Ubuntu /linux as a market competitor, just from the problems i've experienced over the years. Hopefully with the AMD merger, ATI will get their act together, but for this user, I will never know, since I won't buy from either of them again. You should get this "driver explanation" Stickyed, I've spent too many countless hours in the ATI threads over the years. [-(

---

