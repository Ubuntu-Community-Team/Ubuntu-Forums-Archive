---
title: "updates broke nvidia driver"
date: 2011-11-24
forum: Multimedia Software
---

### Post by pickarooney on 2011-11-24
I'm running xubuntu 10.10 and yesterday I ran a bunch of standard updates including the kernel and nvidia modules. Now X won't start unless I change to the open source nv drivers in xorg.conf. When I try enable the latest nvidia drivers, jockey throws the following erros (in jockey.log)

```
XorgDriverHandler.enable(): package or module not installed, aborting
2011-11-24 21:08:38,869 DEBUG: nvidia_current the driver is not enabled in all of the relevant device sections
2011-11-24 21:08:38,895 DEBUG: nvidia_current the driver is not enabled in all of the relevant device sections
2011-11-24 21:09:08,632 DEBUG: nvidia_current the driver is not enabled in all of the relevant device sections
2011-11-24 21:09:08,653 DEBUG: nvidia_current the driver is not enabled in all of the relevant device sections
2011-11-24 21:09:08,821 DEBUG: nvidia_current the driver is not enabled in all of the relevant device sections
2011-11-24 21:09:08,854 DEBUG: nvidia_current the driver is not enabled in all of the relevant device sections
2011-11-24 21:09:09,114 DEBUG: nvidia_current the driver is not enabled in all of the relevant device sections
2011-11-24 21:09:09,147 DEBUG: nvidia_current the driver is not enabled in all of the relevant device sections

```

I think I need to go back to a previous driver version but am not sure how.

My card is a GT218 [GeForce 210]

---

### Post by ptrakk on 2011-11-24
have you tried "apt-get install -y -reinstall nvidia-current"
then maybe "dpkg-reconfigure xserver-xorg"
what i ended up doing was getting the drivers from the nvidia site then when it gets done go to the properties of it and mark it as exectuable. then ctrl + alt + F1. then CTRL + C. "~/Downloads/NV*"

---

### Post by pickarooney on 2011-11-30
> **ptrakk said:**
> have you tried "apt-get install -y -reinstall nvidia-current"
then maybe "dpkg-reconfigure xserver-xorg"
what i ended up doing was getting the drivers from the nvidia site then when it gets done go to the properties of it and mark it as exectuable. then ctrl + alt + F1. then CTRL + C. "~/Downloads/NV*"

I ended up doing the same and it sorted the problem out.

---

### Post by pickarooney on 2011-12-08
This happened AGAIN today after a kernel update and took me an hour to fix. What the hell is wrong with this stupid distro?

---

