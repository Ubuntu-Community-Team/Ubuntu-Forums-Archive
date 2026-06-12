---
title: "screen freeze with nvidia geforce fx 5200 over 8.04"
date: 2008-06-22
forum: Multimedia Software
---

### Post by yuvalz on 2008-06-22
hi,
ive just installed ubuntu 8.04 and just cant use it :
the screen freeze couple of second after im logging in.

after sniffing around a few forums i did as follow  :
1 - installed the latest nvidia driver with the following cmd : sudo sh NVIDIA-Linux-x86-173.14.09-pkg1.run --kernel-source-path=/lib/modules/2.6.24-16-generic/build -k $(uname -r)

the setup seemed to works fine(including the xconfig).
2- the xorg.conf included after the setup :
   in the module section :
   Load "glx"
  #Load "dri"
  in the device section :
   driver  "nvidia" 
 in the screen section :
   option "NvAGP" "0"
3- in the : "/etc/udev/rules.d/90-modprobe.rules" i've added :
    RUN+=="/sbin/modprobe nvidia" 
4- while pressing "modprobe -l | grep nvidia"  i get :
    nvidia.ko
    nvidia_apg.ko (or something like that..)
5- also tried to install older version of geforce 7667 (which was recommanded) but i had some problems with installing...

buttom line : current status after all this is that xserver cant work! 
i get error messages as : "failed to load the kernel module" 
and "no screens found" (i also configured my LG screen in the xorg.conf)

really appreciate any help .. thanks (p.s. the card works great on windows-so its not hw problem..)

---

### Post by Pjotr123 on 2008-06-22
Disable the visual effects:
[http://ubuntutip.googlepages.com/tipsandtweaks](http://ubuntutip.googlepages.com/tipsandtweaks)
(number 5 )

---

### Post by yuvalz on 2008-06-24
thanks but it didnt help.
the "visual effects" are already set to none by default.
my screen freeze either by using :
driver "nv" / "nvidia" / "vesa"
in the  xorg.conf.

anyway, thanks for the help ..
other ideas ??

---

