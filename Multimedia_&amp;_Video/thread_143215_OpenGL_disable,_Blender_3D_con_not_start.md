---
title: "OpenGL disable, Blender 3D con not start?"
date: 2006-03-12
forum: Multimedia &amp; Video
---

### Post by 9192 on 2006-03-12
My system is Sharp MM20.  Ubuntu 5.10 is the only one I can use in the system with wireless network working.  HOwever, X is broken.  I need to comment GLX, DRI and GLCore modules to get X working.  THis disable 3d accelaration and OpenGL.  
I installed Blender 3D but the application did not run at all.

Is it because OpenGL disable?

Anyone using Sharp MM20 and can get all work, wireless, and OpenGL?

Thanks,

9192

---

### Post by Teroedni on 2006-03-12
I think Blender 3d require opengl in order to work, so you need to get 3d working.


After what i found out it seems you laptop uses a monility radeon with 16mb of ram

Have you tried to install thefglrx drivers from ati, or perhaps the radeon driver will work?

---

### Post by 9192 on 2006-03-13
Could nit install the driver.
I downloaded the driver onto desktop and got to terminal.
Whatelse should I do?  wht command, please.
From Ati web, it said it need root to install the driver.
I am a newbie, first time in Linux and Ubuntu.

Thanks,

9192

---

### Post by JohnnyLee on 2006-04-23
The fglrx modules are in the linux-restricted-modules package. You should just be able to install those from synaptic or whatever package manager you use and change the driver in your xorg.conf file from "ati" or "radeon" or whatever it is to "fglrx" and it should (might) work. 

Please post back with your experiences - I've got an MM20 and am interested in putting ubuntu on it and would like to hear how this goes.

---

### Post by JohnnyLee on 2006-05-12
I recently purchased an MM20 and ran into the same problem with openGL. There is a kernel patch available that is not yet merged into Ubuntu, but you can apply it and  recompile the kernel yourself to get AGP and OpenGL working properly. You can find the patch here. 

[http://bugzilla.kernel.org/show_bug.cgi?id=4513]("http://bugzilla.kernel.org/show_bug.cgi?id=4513")

The patch effects the efficeon-agp module. 

I've submitted a bug report with Ubuntu, and am hoping this patch makes it into the Dapper release.

---

