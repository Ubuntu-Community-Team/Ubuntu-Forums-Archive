---
title: "installing NVIDIA driver on kubuntu 10.04"
date: 2010-05-20
forum: Multimedia Software
---

### Post by sunflowers on 2010-05-20
Hi.
I want to install new nvidia driver for geforce 8600 on ubuntu 10.04 but I recive the following error:
[COLOR="Blue"]**The binuteals is not installed on the system.**[/COLOR]
so what should I do to solve it?
Thanks.

---

### Post by ankspo71 on 2010-05-20
Hi,
Have you tried going to Applications > System > Hardware Drivers ? That will launch jockey-kde and will be able to find and install nvidia drivers for you.

If you already tried that and want to install a different driver, I think the name of the package you are looking for is "binutils". You can install that with Kpackagekit, Synaptic Package Manager (if installed), or paste the following command in the terminal:
```
sudo apt-get install binutils
```
Hope this helps.

Edit: you might need binutils-dev too.

---

