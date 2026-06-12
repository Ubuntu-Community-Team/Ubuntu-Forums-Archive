---
title: "how to install latest nvidia drivers?"
date: 2008-04-28
forum: Multimedia Software
---

### Post by herchu on 2008-04-28
Hello,

I am trying to enable latest nVidia video drivers on my Kubuntu Gutsy. I have been using shipped (restricted) drivers for my nVidia video card and the Intel Pro Wireless 3945. I kind of successfully installed newest drivers, but disabled other things in the process, so I wanted to ask for your advice...

What I did was the following: first removed package nvidia-glx-new, and installed the NVIDIA-Linux-x86-169.12-pkg1.run from nvidia download site. The nvidia xorg module did not load at boot, as the module reported as loaded into the kernel was 100.x (as opposed to the just installed 169.x). I did not find a way to void loading that module, except by also uninstalling nvidia-kernel-common. With that change the nvidia module worked ok, latest version.

The problem is that linux-restricted-modules-2.6.22-14-generic (the version I am using) depends on nvidia-kernel-common, so I uninstalled it in the process. And after boot, my wireless card drivers stopped working: in kde Restricted Drivers dialog it complains about not having linux-restricted-modules-2.6.22-14-generic installed.

So my question is: Is it possible to install the latest version of nvidia drivers, and still keep restricted drivers enabled so ipw3945 still works? I have not found any how-to explaining how to **not** use the drivers from ubuntu install...


I am now back to vesa driver, but ipw3945 enabled -- networking is more important for work than 3D!

---

### Post by herchu on 2008-04-28
errr... nevermind, sorry. I went over again on the sticky tutorial on this forum, and found that I forgot or skipped to blacklist the restricted kernel driver.... I am running now the latest nvidia driver with restricted drivers installed.

Thanks tseliot for that great tutorial!

---

