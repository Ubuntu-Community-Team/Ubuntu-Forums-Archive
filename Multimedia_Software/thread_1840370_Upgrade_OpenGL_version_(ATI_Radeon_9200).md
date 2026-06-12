---
title: "Upgrade OpenGL version? (ATI Radeon 9200)"
date: 2011-09-07
forum: Multimedia Software
---

### Post by K1251 on 2011-09-07
Hi

Just changed the graphics card (old one broke) in an oldish computer. The new card is an ATI Radeon 9200. It seems from what I've read that unity should be supported, however:

```
/usr/lib/nux/unity_support_test -p
```
returns:```
OpenGL vendor string:   Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI R200 (RV280 5961) 20090101 x86/MMX/SSE2 TCL DRI2
OpenGL version string:  1.3 Mesa 7.10.2

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      no
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       no

Unity supported:          no
```

Seeing as it says it must have openGL 1.4 to run, and I seem to have 1.3, is there any way to upgrade this? Or is it just not a good enough card?

Oh and this. Just in case anyone was going to ask for it.

```
lspci -nn | grep VGA
```gives me this```
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc RV280 [Radeon 9200] [1002:5961] (rev 01)
```

Thanks!

-K

---

### Post by K1251 on 2011-09-07
Anyone?

To add to my troubles, resizing windows is now infuriatingly slow.

EDIT: I think this part is a driver thing. I don't know whether to use fglrx or the open source ati one. Don't know what I'm using right now, to be honest.

---

### Post by pme 72 on 2011-09-07
I would steer clear of attempting to install the fglrx driver for the Radeon 9200. According to the Natty Installation Guide:

 [http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide#Removing_Catalyst.2Ffglrx](http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide#Removing_Catalyst.2Ffglrx)

"Only RadeonHD chips are supported (by fglrx) on recent Linux distros."

Not sure if the mentioned Updated Open Source Driver PPA's could prove to be helpful with the slow resizing windows problem. Hopefully someone more knowledgeable will post a reply. 

To reveal the chip set and driver currently in use:

```
sudo lshw -c display
```

You will probably see a line similar to this towards the bottom of the return: 
configuration: driver=radeon

---

### Post by jocko on 2011-09-08
> **K1251 said:**
> Seeing as it says it must have openGL 1.4 to run, and I seem to have 1.3, is there any way to upgrade this? Or is it just not a good enough card?
The only way to upgrade is to get a newer card. The R200 cards are not compatible with any opengl version newer than 1.3... [http://en.wikipedia.org/wiki/Comparison_of_AMD_graphics_processing_units#Radeon_R200_.288xxx.2C_9xxx.29_series](http://en.wikipedia.org/wiki/Comparison_of_AMD_graphics_processing_units#Radeon_R200_.288xxx.2C_9xxx.29_series)

And: Don't try to install fglrx. It won't work.

---

### Post by .... on 2011-09-08
Use Unity 2D if you like Unity.

---

### Post by rattskjelke on 2011-10-06
I have the same card and I could not get mine to work either.

---

