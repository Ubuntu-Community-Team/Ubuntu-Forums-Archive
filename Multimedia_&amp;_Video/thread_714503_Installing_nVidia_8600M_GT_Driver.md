---
title: "Installing nVidia 8600M GT Driver"
date: 2008-03-03
forum: Multimedia &amp; Video
---

### Post by cineris on 2008-03-03
Ok, I've downloaded the driver for my graphics card, and I know how to install it and all, but when I try, it says that I don't have the libc headers installed.  How do I install those headers?  I'm fairly new to Linux.....  Thanks in advance for help!

---

### Post by waynewguy on 2008-03-03
I get the same problem. I am installing the 8 series driver for my nVidia 8400 GS. Two problems I have run into so far are the aforementioned one, but that comes only after I can't connect to the nVidia FTP site to see if they have a kernal interface (not really sure what that means). I have a pretty good idea that the reason I can't connect to the ftp has something to do with the runlevel at which X starts up. What I don't know is where to go from here? is it worth changing the runlevel or deal with the libc headers. hope someone can help.

Thought I'd add a link to the nVidia driver:
[http://www.nvidia.com/object/linux_display_ia32_169.12.html](http://www.nvidia.com/object/linux_display_ia32_169.12.html)

there are some instructions in the readme but I believe they're a bit over my head.

---

### Post by uberlube on 2008-03-03
Why not use envy to install the drivers. If you are missing any dependencies it will prompt you if you would like to install them.

---

### Post by waynewguy on 2008-03-04
That did it, here's the link although it can be found elsewhere:
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

However, this did not solve my issue - that I can't get 3D working in ubuntu. I really really want to use compiz fusion but I have not been able to get it to work yet :(


edit: yay I got it working all I had to do was to change the visual effects section under appearance to custom. I love this thing :)

---

### Post by Ostap_VIT on 2008-03-29
> **cineris said:**
> Ok, I'v but when I try, it says that I don't have the libc headers installed.  How do I install those headers? 

su [root password]
apt-get install libc6-dev

---

