---
title: "Why does .22 depend on nvidia-xxx-libvdpau and not just libvdpau1"
date: 2010-04-10
forum: Mythbuntu
---

### Post by rodercot on 2010-04-10
Hey All,

 If you install nvidia drivers from the NVIDIA ppa site it does not require 185-190-195 libvdpau it uses libvdapau1 and libvdpau1-dev instead.

 Why can't the dependency in mythtv be changed to libvdpau1 only because when you try and install both libvdpau1 and nvidia-xxx-libvdpau you always get a dpkg crash due to file overwrite issues and need to force the install.

 Not to mention I have had my /usr/include/vdpau files corrupted in the past. 

 maybe there is a straight foward explanation here which I would like to know about. 

 Thanks,

 Dave

---

### Post by tgm4883 on 2010-04-10
> **rodercot said:**
> Hey All,

 If you install nvidia drivers from the NVIDIA ppa site it does not require 185-190-195 libvdpau it uses libvdapau1 and libvdpau1-dev instead.

 Why can't the dependency in mythtv be changed to libvdpau1 only because when you try and install both libvdpau1 and nvidia-xxx-libvdpau you always get a dpkg crash due to file overwrite issues and need to force the install.

 Not to mention I have had my /usr/include/vdpau files corrupted in the past. 

 maybe there is a straight foward explanation here which I would like to know about. 

 Thanks,

 Dave

It doesn't anymore, you need to enable auto-builds [http://www.mythbuntu.org/auto-builds](http://www.mythbuntu.org/auto-builds)

---

### Post by rodercot on 2010-04-10
Well thats pretty straight-foward - LOL. OK! I am trying to install the frontend only from element Xubuntu 2.6.31.20. 

 Ok so enable auto-builds, update and then install myth-frontend, mythtv-common and libmyth.22.

 THX,

 Dave

---

