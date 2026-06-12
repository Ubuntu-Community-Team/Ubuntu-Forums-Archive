---
title: "VDPAU - will it be standard in Mythbuntu 9.10?"
date: 2009-08-31
forum: Mythbuntu
---

### Post by williammanda on 2009-08-31
Hello
Will VDPAU be be apart of Mythbuntu 9.10 or will we have to go through some extra setup to invoke it?
Thanks

---

### Post by SiHa on 2009-09-02
I understand that VDPAU will be included in MythTV 0.22. If this is released in time to be included in 9.10, then yes.

---

### Post by hackmeister on 2009-09-02
I'm hearing Mythbuntu 9.10 will have MythTV 0.22 as the default version. So yes to VDPAU and support for the Hauppauge PVR-1212 out of the box.

---

### Post by Cyclone42 on 2009-09-02
I don't think people understood the original question. Correct me if I am wrong, but I think the OP meant about the distribution supporting VDPAU.  This is completely different than MythTV supporting VDPAU.

Right now, to get VDPAU support in a Ubuntu installation, you have to go through extra steps: making sure the Ubuntu-supplied Nvidia drivers are not installed, downloading the Nvidia drivers from the Nvidia site, disabling the window manager and dropping to a shell, installing the drivers, and rebooting.  It would be nice if Ubuntu -- *not* MythTV -- supported VDPAU, so these steps wouldn't be necessary.

---

### Post by tgm4883 on 2009-09-02
> **Cyclone42 said:**
> I don't think people understood the original question. Correct me if I am wrong, but I think the OP meant about the distribution supporting VDPAU.  This is completely different than MythTV supporting VDPAU.

Right now, to get VDPAU support in a Ubuntu installation, you have to go through extra steps: making sure the Ubuntu-supplied Nvidia drivers are not installed, downloading the Nvidia drivers from the Nvidia site, disabling the window manager and dropping to a shell, installing the drivers, and rebooting.  It would be nice if Ubuntu -- *not* MythTV -- supported VDPAU, so these steps wouldn't be necessary.

Let me highlight the important bits for you.

> **hackmeister said:**
> I'm hearing **Mythbuntu 9.10 will have MythTV 0.22 as the default version**. So yes to VDPAU and support for the Hauppauge PVR-1212 out of the box.

---

### Post by williammanda on 2009-09-06
I got part of the question answered but I guess I wasn't specific enough. It seems mythtv will support VDPAU but will other media programs in ubuntu have the VDPAU support like Xine? Also I never requested any info on the Hauppauge PVR-1212. I not sure how that got involved in this inquiry.
Thanks

---

### Post by joshoekstra on 2009-09-06
It will support, just as well as Ubuntu Jaunty does. To get it working you'll need to get your hands dirty a bit and install the nvidia-driver that support it. You also might need to install special packages for mplayer and xine to be able to use VDPAU.
Making VDPAU work with mplayer was relatively easy by adding repos with drivers and special packages for mplayer. Mythtv will support it as of .22, which seems to be included in karmic(like it that it's included instead of stable .21).

---

