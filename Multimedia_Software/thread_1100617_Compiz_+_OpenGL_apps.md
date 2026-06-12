---
title: "Compiz + OpenGL apps"
date: 2009-03-19
forum: Multimedia Software
---

### Post by oofnik on 2009-03-19
Not sure if this belongs here, but I'm having a problem running OpenGL applications while running Compiz in Hardy.
I do 3D CAD work in VirtualBox with the OpenGL driver enabled. It works wonderfully only if I turn the fancy effects off. If I try to use it with Compiz on, it appears that the screen doesn't redraw properly. Windows that were closed continue to flash on and off more or less randomly, until my workspace becomes cluttered with 'window ghosts' to the point where it's unusable. Native GL apps have similar behavior.

Is there any way to fix this other than turning off effects when I want to do some modeling?
Oh and I have an Intel 945GM graphics chipset on my Lenovo X60.

Thanks for any help.

---

### Post by Melcar on 2009-03-19
It happens with all drivers (except nvidia).  There is really no way around it currently, other than turning desktop effects off.

---

### Post by oofnik on 2009-03-19
Hm, that sucks. :(
Is there an official bug report for this that I can follow or something?

---

### Post by binbash on 2009-03-19
You may want to send an e-mail to ATI for making better drivers.

---

### Post by Melcar on 2009-03-19
What does ATI have to do with his particular issue?  He's running an Intel chip.  Every single driver, be it open source or proprietary, suffers from blinking opengl applications when a composition manager is running.  It's a limitation of the current X structure and is being worked on.  
The easiest thing to do is to create icons on your panel that switch Compiz on/off; when you're about to run an opengl app. simply turn Compiz off.  You can also make a script that shuts down Compiz when a 3D app. is launched; a bit more complicated to do, but its another option that works.

---

