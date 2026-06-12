---
title: "Official Nvidia drivers, 10.10, and compiz, AGAIN"
date: 2010-11-22
forum: Multimedia Software
---

### Post by Afisamuleal on 2010-11-22
Hi, thanks for your time:

I've been using ubuntu for 6 years. My current laptop has NEVER worked with the built in Nvidia drivers, ie, glx has never functioned properly, no matter how many google searches and forum threads I read.

So, I've been using the official Nvidia driver for a couple years.

However, today, when I upgraded to v10.10, I find my Nvidia driver doesn't work. I decided to give the non-official drivers a try, however, I have encountered one of the usual problems that "This driver is activated but not currently in use", for which the interweb returns me "Resolved" unresolved threads, and general comments on uninstalling all of Ubuntu's nvidias and reinstalling the specific nvidia.

Perhaps my Official Nvidia driver is interfering with this? I did some searches on how to uninstall the Official Driver, but my Googling skills are weaker than they used to be, because all I can find is how to use synaptic to uninstall nvidia-glx (which doesn't exist, among countless other packages that have never ever existed) or nvidia-*.

Anyway, I want compiz to work, so I need composite. I'd appreciate any help you can give me; specifically, instructions for uninstalling Official Nvidia drivers, and instructions on how to compensate for the "activated but not in use" bug if my solution-postulation is incorrect.

Machine info:
P7805-u Gateway laptop with Nvidia GeForce 9800m GTS (1GB) Graphics, 1900x* screen, Ubuntu 10.10, attached xorg.conf file.

Sam

---

### Post by b0b138 on 2010-11-22
You need the install file to uninstall. Use this command
```
sudo sh NVIDIA* --uninstall
```
I would also suggest adding this ppa to you sources list to install a newer driver than what the official repos do. [https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

---

