---
title: "nvidia restricted drivers on kubuntu"
date: 2007-06-13
forum: Multimedia &amp; Video
---

### Post by xargon on 2007-06-13
Hi everyone,

I am running ubuntu 7.04 but want to move to kubuntu. However, I love the restricted driver manager in ubuntu which installed the nvidia driver with one click.

I was wondering if something like that is there in kubuntu or what is the process of installing the restricted nvidia drivers on it. Also, will I be able to use the program nvidia-settings on it?

Cheers,
xarg

---

### Post by Nythain on 2007-06-13
you can install the drivers easy enough by installing the nvdia-glx package of your choice for your card

sudo apt-get install nvidia-glx-new
for the 9755

sudo apt-get install nvidia-glx
for the 9631

sudo apt-get install nvidia-glx-legacy
for really old and now unsupported cards

if you miss restricted drivers that much you can install the restricted driver manager that ubuntu uses
sudo apt-get install restricted-manager

---

