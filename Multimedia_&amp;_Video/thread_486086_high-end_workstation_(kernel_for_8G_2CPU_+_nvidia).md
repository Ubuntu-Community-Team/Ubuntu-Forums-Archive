---
title: "high-end workstation (kernel for 8G 2CPU + nvidia)"
date: 2007-06-27
forum: Multimedia &amp; Video
---

### Post by jkogut on 2007-06-27
Hello,

I am trying to deploy Ubuntu 6.10 (Egdy) on so called "high-end workstation".
I have got  2 CPU  + 8G RAM with 32-bit environment.  
Because I want to do it Ubuntu way (since it is a binary distro), I look for kernel supporting 8G RAM. 
The only choice is:  2.6.17-11-server
2.6.17-11-generic ----> does not support more than 4G RAM
2.6.17-11-i386    -----> does not support more than 4G RAM + SMP

Thats OK. I am happy with many choices I have ;-) 
The next step is 3D support for video card. 

apt-cache search nvidia ---> apt-get install nvidia-glx  oooops! here we go! I can't install it unless I use 2.6.17-11-(generic/i386) kernels ;-( 

My question is:
How to do it properly to be compliant with Ubuntu way ?

Cheers,
Jan Kogut

---

### Post by hardyn on 2007-06-27
check out the instructions on the nvidia website, the installer looks like it has been cleaned up a little;

what is the ubuntu way, exactly?

---

### Post by jkogut on 2007-06-27
> **hardyn said:**
> 
what is the ubuntu way, exactly?

debian/ubuntu way: 
apt-get update
apt-cache search nvidia
apt-get install nvidia-glx
#nvidia-glx-config enable

enjoy ;-)

evil way:
apt-get install linux-headers-$(uname -r)  ....... and a lot of stuff for example kernel-package

then there is a lot of diffrent ways:
--playing with make-kpkg and "nvidia friendly linux-image" (modules)
--wget NVIDIA........sh etc
--comiling everything ??? (am I on Gentoo???) 
--make coffee ;-)
--play S.T.A.L.K.E.R. ;-)


Cheers,
Jan Kogut

---

### Post by hardyn on 2007-06-27
yeah your prolly doing it the non ubuntu way; unless somebody from the community will compile you a package?

---

### Post by jkogut on 2007-06-28
Well, locally (just for my needs) I can do it myself (precompiled nvidia kernel modules for 2.6.x-server).
I just was curious about it (installing properly) ;-)

I still think that Debian/Ubuntu have done great job in terms of idea "let the robot do it for you" ;) and sooner or later Ubuntu will be mature enough to compete with SuseLinuxEntDeskt, Vista etc (in case of high-end environment).

Cheers,
Jan Kogut

---

