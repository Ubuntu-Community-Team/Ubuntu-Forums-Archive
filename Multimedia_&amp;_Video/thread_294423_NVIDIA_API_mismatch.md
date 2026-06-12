---
title: "NVIDIA API mismatch"
date: 2006-11-06
forum: Multimedia &amp; Video
---

### Post by KlausU on 2006-11-06
Hi,

lately (probably since last nvidia update) everything using OpenGL fails, i always get the following error: 

> 
Error: API mismatch: the NVIDIA kernel module has the version 1.0-8774, but 
this client has the version 1.0-8776. Please make sure that the kernel 
module and all NVIDIA driver components have the same version 


I got the following installed:
nvidia-glx in 1.0.8776+2.6.17.6-1 and
nvidia-kernel-common in 20051018+1ubuntu7 

Anyone with the same problem or any idea for an solution?

---

### Post by evilghost on 2006-11-06
sudo apt-get install nvidia-glx --reinstall
reboot

---

### Post by KlausU on 2006-11-06
It seems that the security source is the source for the breaking package... somehow the nvidia-glx is updated but not the kernel modification. Shouldn't all nvidia users have this Problem?

---

### Post by Fator dee on 2006-11-06
I've been having problems with my graphics card too. Since the last update I have been unable to play Dark Crusade and Anarchy Online with cedega, because they don't recognize the card anymore, although everything else works fine.

---

### Post by KlausU on 2006-11-06
> **Fator dee said:**
> I've been having problems with my graphics card too. Since the last update I have been unable to play Dark Crusade and Anarchy Online with cedega, because they don't recognize the card anymore, although everything else works fine.

Have you tried glxgears?

---

### Post by Fator dee on 2006-11-06
> **KlausU said:**
> Have you tried glxgears?

Just tried it, works fine.

---

### Post by KlausU on 2006-11-06
I just installed the nvidia-glx=1.0.8774+2.6.17.5-11 manually, resulting in a failing X startup... Now had to fall back to "nv".. making xinerama fail and still no glx applications (Xlib:  extension "GLX" missing on display ":0.0")

---

### Post by KlausU on 2006-11-06
Now this was the Xorg.0.log [http://www.ubuntuusers.de/paste/4977/](http://www.ubuntuusers.de/paste/4977/)
well I reinstalled nvidia-glx with the latest Version... and it mystically works fine now. Heh thanks --reinstall would probably have worked aswell, heh.

Thanks anyways and have a nice day :)

---

