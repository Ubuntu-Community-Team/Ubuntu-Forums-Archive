---
title: "Running KDE / X on server kernel vs 386"
date: 2007-08-07
forum: Multimedia &amp; Video
---

### Post by CopaceticOpus on 2007-08-07
I have had a crazy time trying to get KDE to load and to set resolutions properly. I finally got things working, but ONLY when I use the "386" variety of the kernel. My GRUB menu shows the following kernel options:

* 2.6.20-16-server
* 2.6.20-15-386
* 2.6.20-15-server

I am running 7.04 Fiesty Server with the package kubuntu-desktop installed. I have a NVIDIA GeForce 6150 and I'm using the nvidia-glx-new drivers.

I've done so many tutorial steps and suggestions that I'm not sure what worked, but I'm puzzled why I have to use the 386 kernel instead of the server kernel. When I use the server kernel I just get a black screen with a blinking cursor (though I can still access the text-based terminals.)

---

### Post by tbroderick on 2007-08-07
The server kernel doesn't have the needed linux-restricted-modules. You should stick to a non-server kernel for a desktop.

---

### Post by CopaceticOpus on 2007-09-05
Thanks!

---

