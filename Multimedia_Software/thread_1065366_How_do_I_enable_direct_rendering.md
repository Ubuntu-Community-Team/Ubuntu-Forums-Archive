---
title: "How do I enable direct rendering?"
date: 2009-02-09
forum: Multimedia Software
---

### Post by kerryhall on 2009-02-09
I have an Nvidia card, the drivers are installed, driver version 177.82, I have the Nvidia X config app installed, Driver 177 shows up under the proprietary drivers as installed and in use, I have Load "dri" under the module section of my xorg.conf. 

But if I do glxinfo | grep rendering I get

Direct Rendering: no

How do I enable direct rendering? Running Intrepid Ibex.

Thanks!

---

### Post by jrusso2 on 2009-02-09
> **kerryhall said:**
> I have an Nvidia card, the drivers are installed, driver version 177.82, I have the Nvidia X config app installed, Driver 177 shows up under the proprietary drivers as installed and in use, I have Load "dri" under the module section of my xorg.conf. 

But if I do glxinfo | grep rendering I get

Direct Rendering: no

How do I enable direct rendering? Running Intrepid Ibex.

Thanks!

Is it a bug seems like it should be working.  How are you Open GL screensavers running?

---

### Post by kerryhall on 2009-02-09
glx gears gives me around 350 fps.

Not great, but my video card was having some overheating problems in the past. 

So you think it could just be a bug with glx info?

Is there any way to test direct rendering besides performance?

---

### Post by kerryhall on 2009-02-14
Bump. 

I tried running some of the NeHe OpenGL tutorials one of the ones that uses freeglut, and it says something like "Unable to create direct rendering context. This may hurt performance"

So there is definitely something wrong.

Also, any attempt to run programs that use GLSL results in a black screen (in the relevant window), and I know a geforce 6600 supports GLSL. Something is definitely wrong here.

---

