---
title: "[SOLVED] nvidia graphics card"
date: 2007-08-19
forum: Multimedia &amp; Video
---

### Post by solarnomad on 2007-08-19
I have a Galaxy 6200LE card running on 6.0-386 (Dapper) . I have installed the linux-restricted-modules and the nvidia-glx. I manually changed the driver to nvidia in xorg.conf and commented out "dri". Upon rebooting the Xserver will not start and reports "Module nvidia not found", despite it being listed as installed by Synaptic Package Manager.
Can anyone help?
Problem has now been solved by using Envy.

---

### Post by logos34 on 2007-08-19
try 

**sudo nvidia-glx-config enable**

reboot

if the video driver shows up with
[B]
lsmod | grep nvidia [/B]

then add it to /etc/modules:

**gksudo gedit /etc/modules**

add **nvidia**

---

### Post by solarnomad on 2007-08-19
try

sudo nvidia-glx-config enable

reboot

if the video driver shows up with

lsmod | grep nvidia

then add it to /etc/modules:

gksudo gedit /etc/modules

add nvidia

Unfortunately it does not show up after being enabled, which seems to do nothing. Any other suggestions would be most welcome.

---

