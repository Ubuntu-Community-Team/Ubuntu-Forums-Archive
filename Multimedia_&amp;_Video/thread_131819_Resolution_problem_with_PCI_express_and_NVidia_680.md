---
title: "Resolution problem with PCI express and NVidia 6800"
date: 2006-02-17
forum: Multimedia &amp; Video
---

### Post by Galad on 2006-02-17
First of all, nice to meet you all.
I have a problem with making Xorg configure my video card properly.
My pc is based upon a pci-express architecture and my video card has an NVidia chipset 6800.

The basic X resolution after installation and system update is 640x480 and I can't change it.

I tried to install Nvidia drivers with:
apt-get install nvidia-glx
apt-get install nvidia-settings

and then using the command:
nvidia-glx-settings (or something similiar)

After the reboot I had the same problem.

I also tried to edit xorg.conf,
commenting the lines:
Load Dri
Load GLCore

and the "Section DRI" but I yet can't solve my problem.

I suppose I'm making something possibly stupid, beacause I have the same problem with Kubuntu on my Pavillion HP DV4000 notebook.

I'd appreciate every kind of suggestion.

As always, I beg your pardon for grammar mistakes.

---

