---
title: "[SOLVED] Radeon 4670 and Ubuntu 8.10"
date: 2008-11-22
forum: Multimedia Software
---

### Post by rmjohnson144 on 2008-11-22
My 8800GT went on the fritz and had to RMA it, I got a 4670 for temporary use and it wouldn't work in ubuntu 8.04 at all until it finally gave me a blank screen.  

anyway, I just reinstalled ubuntu 8.10 in hopes of getting it to work by default.  I boot up and it works fairly well.  I get 1440x1050 or something by default and it looks good and plays video fair.  I install the default proprietary drivers from the Hardware Drivers menu.  It gives me my full 1680x1050 resolution, but video is very, very choppy.  I feel like a strobe light is turned on.  I followed the multimedia post to setup vlc and use deinterlace modes, but none of them work.  Some have less flicker, but they all are unbearable.  I even tried using EnvyNG with the samee results.  I think it uses driver 8.53.4 on both driver versions.  I tried ATIs website and they don't list 4670 as being supported.  I tried looking for beta drivers there as well, but couldn't find a beta section.

anyone know how to make this work?
-=Mark=-

---

### Post by rmjohnson144 on 2008-11-24
My system went down and had to return it.  I then hooked up my hard drive to my P5Q Dlx which has the same chipset as the P5Q3 Dlx except it has DDR2 instead of DDR3 memory.  It also has a 4870X2 instead of a 4670.

Anyway, I got rid of the Flicker by disabling the visual effects in the System--> Preference--> Appearance then to the Visual Effects tab and selecting None.  It was set to Normal by default.  Now I get great video once again.

I found this info at the Unofficial ATI Linux Driver Wiki under Unbuntu.

Here is the link to the Intrepid (Ubuntu 8.10) section.
[http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide)

-=Mark=-

---

