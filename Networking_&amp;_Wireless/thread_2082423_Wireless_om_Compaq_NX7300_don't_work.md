---
title: "Wireless om Compaq NX7300 don't work"
date: 2012-11-09
forum: Networking &amp; Wireless
---

### Post by stupidslug on 2012-11-09
After installing Ubuntu 12.10 on a Compaq NX7300, the wireless network is not working. It's a completely new installation on a blanked hard drive.

Can any of You please help to get it working?

Please, a GUI solution. Not involving the command line.

---

### Post by chili555 on 2012-11-09
> Can any of You please help to get it working?Certainly.> Please, a GUI solution. Not involving the command line. Probably not. I am unaware of any GUI method to gather the necessary data in sufficient detail in a GUI. As well, there are drivers that can be installed by GUI in eight or ten steps or by command line in one copy-n-paste command. If you are willing to be just a bit flexible, please open a terminal and run and post:```
lspci -nn | grep 0280
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

---

### Post by stupidslug on 2012-11-09
Unfortunately, using the command line is completely out of the question. It's an imperative for the user of the actual computer to complete the task by GUI.

I know the BCM wl has been previously working, but as the installation process involves several CLI steps it's not a workable solution. Unfortunately I does not remember wich chip it carries. Probably a b43??

Something like firing up Synaptic and point to a packet for installation is the only acceptable way to go. But wich packet to install?

---

### Post by chili555 on 2012-11-09
> Unfortunately I does not remember wich chip it carries. Probably a b43??Without that information, we can't possibly know this...> But wich packet to install? If you can get the pci.id, something like 14e4:45xy, we probably can use Synaptic.

---

