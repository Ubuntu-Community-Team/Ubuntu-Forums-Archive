---
title: "Need to first find out - If I have a Problem"
date: 2007-03-19
forum: Multimedia &amp; Video
---

### Post by GMU_DodgyHodgy on 2007-03-19
First let me give you a run down of my system:

Running Ubuntu Edgy Eft (6.10)
AMD Athlon 1.4 Ghz
1 Gigabyte of RAM
NVIDIA Gforce card 128 MB (not sure of exact chip or driver).

I have been running Ubuntu for a couple of weeks.  My monitor works fine and I am able to do most everything I need.  However, I have not tried any 3-D games or desktop effects.  

I read through these forums, but have need to know the following:

1.) How do I determine which Nvidia chip and Driver am I using.  This will help determine if I have a problem with driver support in Ubuntu.

2.) How do I determine if my current set-up can handle 3-D acceleration?  

3.) If I determine that my current configuration does not support 3-D acceleration - how which of the methods offered in the Sticky How-Tos should I use?

Sorry of these are dense question - but I am a relative Noob to Linux and just want to approach this issue from a high level (i.e. determine if I do have a problem first -then jump into a solution).

Thanks in advance.

---

### Post by H3g3m0n on 2007-03-19
'lspci | grep -i vga" in a console should tell you your exact graphics card

"glxinfo" should tell you if you are able to do 3d and you can test with "glxgears", otherwise just install something like billiards or one of the OpenGL chesses from the repositories and see if they refuse to load, or are slow.

By default you will be using th nv driver which doesn't support hardware acceleration unless someone else set up the driver, so you will probably need to install the correct drivers (this is covered in enough places already).

You can check if this is the case by looking through the /var/log/Xorg.0.log file and see if its nv or nvidia being loaded. Or maby the /etc/X11/xorg.conf might be easier to read.

---

### Post by GMU_DodgyHodgy on 2007-03-19
> **H3g3m0n said:**
> 'lspci | grep -i vga" in a console should tell you your exact graphics card

"glxinfo" should tell you if you are able to do 3d and you can test with "glxgears", otherwise just install something like billiards or one of the OpenGL chesses from the repositories and see if they refuse to load, or are slow.

By default you will be using th nv driver which doesn't support hardware acceleration unless someone else set up the driver, so you will probably need to install the correct drivers (this is covered in enough places already).

You can check if this is the case by looking through the /var/log/Xorg.0.log file and see if its nv or nvidia being loaded. Or maby the /etc/X11/xorg.conf might be easier to read.

H3g3m0n,

Thank you for your response. I will follow your instructions.  I don't think my 3-d acceleration is activiated because I did try 3-d chess and it froze.  I will look into the Envy project as it seems to have automated the process.

Cheers. 
HodgyDodgy

---

