---
title: "Computer very slow with multimedia"
date: 2007-10-26
forum: Multimedia Production
---

### Post by henrywm on 2007-10-26
I am testing Ubuntu on an old Dell Inspiron 2650 with the following specs:

CPU: 1.7GHz
Memory: 256
Video card: NVIDIA GeForce2 Go Vid
Hard drive: 30GB

When this computer used Windows I was able to play some games with heavy multimedia with little or no trouble. Now Linux games with even medium graphics run very slowly. Why? Is the current distro of Ubuntu too demanding for my system? I had the same problem with Fedora.

---

### Post by scrooge_74 on 2007-10-26
Try instally Xubuntu, it will be easier on the resources

---

### Post by ddrichardson on 2007-10-26
Which version of Windows?

---

### Post by nalmeth on 2007-10-26
What version of Ubuntu are you using?

Have you installed the Nvidia Proprietary Driver?

---

### Post by henrywm on 2007-10-27
It originally used Windows XP Home. When I started this thread I was using Feisty. I upgraded to 7.10 last night.

Today I enabled NVIDIA in the Restricted Drivers dialogue. Now when I start the computer the screen works only on the left half of the screen and flickers. It also goes black before I can even login.

---

### Post by henrywm on 2007-10-27
Apparently the NVIDIA drivers are causing problems. This brings a few questions?

1) Can I disable the drivers and revert back to the default without reinstalling Ubuntu?

2) If I need to reinstall Ubuntu, can I keep the data in my Home folder and keep the permissions to read and edit the files?

3) Is there an alternative driver that will allow me to use 3D graphics without ruining my system like this one did?

---

### Post by scrooge_74 on 2007-10-27
1. Go to /etc/X11/xorg.conf and look for a section call Device and a line which says driver, you have to change the driver to nv
2. to keep all of your data from your /home folder you have to have it in a separate partition, if you have it like this when you reinstall you only have to create the user with the same name as the folder and he will own everything in there.
3.The only drivers are those, it sometimes depend on the version of Ubuntu you are using and/or if the driver for that particular card is good enough

---

### Post by henrywm on 2007-10-27
I cannot do that, because the screen goes black before I can even login. I am posting this message from another computer.

---

### Post by ddrichardson on 2007-10-27
Ubuntu is going to struggle in such a small memory footprint - Xubuntu is a better bet.

Yes you can disable the driver by editing xorg.conf. Generally it's better to have a working backup torevert to if all else fails.

You can keep your home folder - if it's on a seperate partition, if not then archive it, reinstall and de-archive it.

---

### Post by ddrichardson on 2007-10-27
> **henrywm said:**
> I cannot do that, because the screen goes black before I can even login. I am posting this message from another computer.Yes you can - pres ctrl-alt-f2 and login to a terminal.

---

### Post by henrywm on 2007-10-27
That did not give me a terminal, but it did allow me to log on as normal and disable the driver in the Restricted Drivers dialog box.

I am not sure what happened. I pushed CTRL-ALT-F2 repeatedly during the system startup. Did it boot the computer with restricted drivers disabled? At any rate, it seems to be working okay now, but it is unfortunate that I cannot use heavy graphics.

The item in the Restricted Drivers box which caused the problem was called "NVIDIA accelerated graphics driver." This computer is using an NVIDIA GeForce 2 Go Vid video card. I bought this computer almost 5 years ago. Does Ubuntu just not support that card? Is there another solution? I do not know how to replace the graphics card in a laptop.

I do not use it for anything anymore, and so it makes a good test machine with which to try Linux, except that I apparently cannot fully test its graphics capability.

---

### Post by henrywm on 2007-10-27
I case something like this or something more serious happens in the future, does Ubuntu have something similar to System Restore in Windows with which to save restore points.

---

### Post by ddrichardson on 2007-10-27
No. The only two things likely to cause problems are kernel updates, in which case the previous is still accessible from grub, or xorg - which is why we recommend backing it up.

There are many people suggesting something like system restore - but it is not a very good system. It uses an enormous amount of hard disk space over time and frequently doesn't work.

Personally I set up my Ubuntu installation and then create a disk image then I can restore when ever there is a problem.

As for your graphics card, I can't really help because the restricted driver is proprietry, if you have problems with it you are more likely to get better support from nvidia's linux forum as Ubuntu doesn't directly support proprietry drivers.

I also cannot find any reference to a GeForce 2 Go card - do you have any more information on the model number?

---

### Post by henrywm on 2007-10-27
I do not have a model  number. Aside from the home directory, which files should I backup?

---

### Post by scrooge_74 on 2007-10-27
Any complicated config in your /etc if everything is standard there then just your /home

---

