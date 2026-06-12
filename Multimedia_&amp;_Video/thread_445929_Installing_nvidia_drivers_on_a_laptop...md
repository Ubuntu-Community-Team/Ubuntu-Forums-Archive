---
title: "Installing nvidia drivers on a laptop.."
date: 2007-05-16
forum: Multimedia &amp; Video
---

### Post by blop on 2007-05-16
HI all, i have got my desktop kubuntu working with my nvidia graphics using Envy but for some reason it failed on my laptop. So i followed the instructions in this post:

[http://doc.gwos.org/index.php/Latest_nvidia_feisty](http://doc.gwos.org/index.php/Latest_nvidia_feisty)

Now i think the driver has changed because on reboot it does 'look' different, the font is definitley different....also looks sharper in general.How can i tell itsdefintley working right and where do i get the Nvidia manager in the applications menu that Envy installs.

cheers

---

### Post by ntetreau on 2007-05-16
You can look at the device section in your /etc/X11/xorg.conf, it should say nvidia

Also, in a terminal run:

```
glxinfo | grep vendor
```

my output:

server glx vendor string: NVIDIA Corporation
client glx vendor string: NVIDIA Corporation
OpenGL vendor string: NVIDIA Corporation


Nic

---

### Post by blop on 2007-05-16
SNAP!

yea me to!

server glx vendor string: NVIDIA Corporation
client glx vendor string: NVIDIA Corporation
OpenGL vendor string: NVIDIA Corporation

but how do i get the management application that Envy installed? Think it lived in the system menu......

---

### Post by dabl on 2007-05-16
> **blop said:**
> SNAP!

yea me to!

server glx vendor string: NVIDIA Corporation
client glx vendor string: NVIDIA Corporation
OpenGL vendor string: NVIDIA Corporation

but how do i get the management application that Envy installed? Think it lived in the system menu......

```
nvidia-settings
```


??

---

### Post by blop on 2007-05-16
cheers thank you!

---

### Post by stchman on 2007-05-16
> **blop said:**
> HI all, i have got my desktop kubuntu working with my nvidia graphics using Envy but for some reason it failed on my laptop. So i followed the instructions in this post:

[http://doc.gwos.org/index.php/Latest_nvidia_feisty](http://doc.gwos.org/index.php/Latest_nvidia_feisty)

Now i think the driver has changed because on reboot it does 'look' different, the font is definitley different....also looks sharper in general.How can i tell itsdefintley working right and where do i get the Nvidia manager in the applications menu that Envy installs.

cheers

If you are using Fesity the Nvidia restriced drivers are just  a click away.  Worked on an ATI and Nvidia equipped laptop.  If you are using Edgy then Envy is needed.

TO get to the nvidia settings you can type

nvidia-settings in a terminal window.

---

