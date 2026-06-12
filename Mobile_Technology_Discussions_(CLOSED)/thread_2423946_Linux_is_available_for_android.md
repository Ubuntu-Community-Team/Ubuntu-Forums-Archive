---
title: "Linux is available for android"
date: 2019-08-01
forum: Mobile Technology Discussions (CLOSED)
---

### Post by mac192 on 2019-08-01
I don't know is it possible to convert android phone to linux OD

---

### Post by TheFu on 2019-08-01
Android **is** Linux already.  There are a few tools you can load to gain access to the command line and use it like a linux server.  For better control, the Android install needs to be root'd.  If your intent is to load some GUI tool, that is a completely different issue, mainly about dependencies in the libraries available, limitations for input devices.  People have loaded Linux desktops into a chroot and run those under Android.  I did that a long time ago on a 10 inch tablet.  The keyboard mapping was a challenge, even with a working USB keyboard, some of the critical keys couldn't be mapped correctly. Running 2 full desktop OSes, like a chroot effectively does requires a strong CPU and plenty of RAM.

Any ability to directly load a Linux desktop OS onto any Android device is extremely limited by the hardware involved.  Some will work. Some will not.  Some that work need hardware modifications. Some do not.

For server stuff, most Android installs should support running Linux Containers. I've not done that, but container support has been in the kernel a very long time and isn't dependent on the CPU architecture.

In no way can 100% of android tablets be made to accept a Linux Desktop install.  Look up your specific model, see what other people hacking it have been able to accomplish.  That is where I'd start.

[https://forum.xda-developers.com/hd8-hd10/development/install-linux-distribution-amazon-hd-10-t3726873](https://forum.xda-developers.com/hd8-hd10/development/install-linux-distribution-amazon-hd-10-t3726873) is an example of a chroot on an Amazon Fire Tablet.  They never got a full install working.

---

### Post by bijayalaxmi1808 on 2019-10-01
If you want to convert Android to Linux, then Android itself is running on top of Linux kernel.
Every Linux distro is linux with some sort of desktop UI and their own package management system.
Android has it's own UI and Play store as it's package management system.

You can root the Android device to install busybox to get more commands and tweak many things to get more control of the Android device.

Also, there are many Linux distro ports available to be installed on many Android running devices.
For example: Ubuntu touch is available for many Android devices
Here is a list of compatible devices: [https://devices.ubuntu-touch.io/](https://devices.ubuntu-touch.io/)

Somewhere I have also seen Kali Linux port for some Android phone.
Well, it is not that it is not possible to run any Linux distro, rather the point is just it needs porting efforts, that's all.

You can Google to get more info to get a certain Linux distro for your device.

By the way, I did not understand what Linux OD means!

---

### Post by bernard010 on 2019-11-28
One of the snaps on Ubuntu 19.10 is UBports installer  (0.4.11-beta) . . Otherwise their is the official website: [https://ubports.com/](https://ubports.com/)   Part of Ubuntu quite interesting what I have read .

---

### Post by bernard010 on 2019-11-29
**Here are a couple of options for Linux on Android** : My choice was Plasma Mobile. Have not tried it yet.
  Plasma Mobile   [https://www.plasma-mobile.org/](https://www.plasma-mobile.org/)

Halium   [https://docs.halium.org/en/latest/](https://docs.halium.org/en/latest/)

  PostmarketOS   [URL="https://wiki.postmarketos.org/wiki/Main_Page"]https://wiki.postmarketos.org/wiki/Main_Page 



[/URL]

---

