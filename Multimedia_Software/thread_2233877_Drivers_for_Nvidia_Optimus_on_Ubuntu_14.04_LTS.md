---
title: "Drivers for Nvidia Optimus on Ubuntu 14.04 LTS"
date: 2014-07-11
forum: Multimedia Software
---

### Post by Thanos_TinyOS on 2014-07-11
Dear all,

Thank you for your time and effort to assist me with my question. I have recently format my laptop and installed ubuntu 14.04 LTS. I am really happy with the performance and new features in comparison to the 12.04 LTS version that I was using before. I was following a really nice tutorial on things to do after installing 12.04 LTS [http://debianhelp.wordpress.com/2012/11/10/to-do-list-after-installing-ubuntu-12-04-lts-aka-precise-pangolin/](http://debianhelp.wordpress.com/2012/11/10/to-do-list-after-installing-ubuntu-12-04-lts-aka-precise-pangolin/) and I tried to install the recommended drivers for my graphics card by adding the repository (sudo apt-add-repository ppa:ubuntu-x-swat/x-updates). When I am trying to update all repositories through (sudo apt-get update) and then upgrade with (sudo apt-get upgrade). In theory I should have no problem by having the latest (stable) graphics drivers.

Unfortunately when I am using 2 screens then problems start to pop up. Most of the times half of the secondary screen appears in my primary screen, and other small problems. I assume that either the installation of the drivers is not correct or need to be redone or their is another reason. I am not expert of linux, I am a relative new user and basic programmer.

Based on the instructions of the tutorial I applied the command (lspci -nnk | grep -iA3 vga) and the output was:

00:02.0 VGA compatible controller [0300]: Intel Corporation 3rd Gen Core processor Graphics Controller [8086:0166] (rev 09)
    Subsystem: Samsung Electronics Co Ltd Device [144d:c652]
    Kernel driver in use: i915
00:16.0 Communication controller [0780]: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 [8086:1e3a] (rev 04)

So my question is:

Does anyone knows if there are better drivers for this particular graphics card?

Thanks in advance for your time and effort reading and replying my question.

---

### Post by patsev-anton on 2014-07-12
is sme bug?
[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/1167301](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/1167301)

---

### Post by Thanos_TinyOS on 2014-07-12
I do not think so, I think I have installed wrong drivers. Is there a process that I can follow to remove the old ones and install the new ones?

Thanks again for your time and effort.

---

### Post by Bucky Ball on 2014-07-12
Welcome. Bumblebee is your friend. It is in the repositories (Software Centre or Synaptic Package Manager). That's what you need for Optimus.

Details:
[http://bumblebee-project.org/](http://bumblebee-project.org/)

Bumblebee may deal with removing the other drivers. Give it a go.

---

### Post by Thanos_TinyOS on 2014-07-13
Hello Bucky Ball,

I think bublebee is the only way too.. :D

I found an installation process really easy to follow to: [http://www.upubuntu.com/2012/10/to-do-list-after-new-installation-of.html?m=0](http://www.upubuntu.com/2012/10/to-do-list-after-new-installation-of.html?m=0)

Maybe some else one also need it.

Thank you for your time and effort replying to my question.

---

### Post by Bucky Ball on 2014-07-13
The easiest way is to install it from the official Ubuntu repositories via the Software Centre, Synaptic Package Manager or the terminal. 

The link you gave is dated and is for 12.10 which is no longer supported (and hasn't been for quite some time). Bumblebee may not have been included in the offical Ubuntu repos then. Always check the repositories first and defer to that version rather than a PPA or manually installing (harder to get support and more prone to breakage).

---

