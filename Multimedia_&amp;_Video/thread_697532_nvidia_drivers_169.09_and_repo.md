---
title: "nvidia drivers 169.09 and repo"
date: 2008-02-15
forum: Multimedia &amp; Video
---

### Post by mohbana on 2008-02-15
hi everyone,

i use fedora and ubunt, ive got a few questions.

1. how come there is no automated way of installing the nvidia drivers, i've got a 8800gts 512mb probably based on the g92 chipset not sure tho.  anyhow in fedora i simply have to enable the livna repo and everything is done for me, its really sad that this is not in ubuntu. Pretty obvious why it should be in the repo, not everyone wants to keep installing the drivers everytime the kernel changes.
2. when i try to enable restricted drivers, it says "your hardware does not need any restricted drivers"!

thanks for your time.

---

### Post by pbcartwright on 2008-02-15
you might want to install envy and let it install your NVIDIA drivers for Ubuntu.. see the web site:
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by mohbana on 2008-02-16
his repos aren't for gusty 7.10.

---

### Post by erginemr on 2008-02-16
I think there is a Gutsy Debian package in ENVY's a/m website, and it should fetch the drivers directly from NVIDIA / ATI web sites.

Alternatively, make sure that you have restricted drivers repository enabled:

from Main Menu -> System -> Administration -> Synaptic Package Manager
and from Synaptic Menu -> Settings -> Repositories

Enable all repositories there, press reload (update) button and re-run the "restricted drivers manager".

PS. Here is another thread on the same card:
[http://ubuntuforums.org/showthread.php?t=693226](http://ubuntuforums.org/showthread.php?t=693226)

---

### Post by mohbana on 2008-02-16
no i am saying it should be pre compiled for the kernel like what they do over at fedora, it makes things much easier for people.

i simply issue this command and its done; su -c 'yum install kmod-nvidia'

---

### Post by erginemr on 2008-02-16
With all due respect, I don't see any difference. Ubuntu repositories also have compiled nvidia binary packages, but they cannot include them with the install as they are not GPL. All you have to do is to enable the restricted drivers repository and install the driver with:
```
sudo aptitude install nvidia-glx-new
```
or better, with the "restricted drivers manager", which is not much harder than:
```
su -c 'yum install kmod-nvidia'
```

---

