---
title: "Heelllpppp upgrading"
date: 2007-11-10
forum: Multimedia &amp; Video
---

### Post by Gotfredsen on 2007-11-10
This is simply not easy coming from Windows. Have en older NVIDIA card when I installed Ubuntu Server 7.04. Now I got a newer NVIDIA card (6200 - passive cooling). Old drivers won't work.
To you gurus: how does one upgrade the drivers to newer drivers that fits the new card. I know where to download the drivers but the driver installation process .. AAAaaarrrrrgggghhhhhhh.

/Lars

---

### Post by Jose Catre-Vandis on 2007-11-10
If your server is just command line interface, this shouldn't be a problem.

If you have installed a desktop to your server, then you will need to install the drivers and reconfigure xorg

Best to remove existing driver first
You probably want "nvidia-glx" (repos) or search for installation guide on the forum.

then in a terminal run:
```
 sudo dpkg-reconfigure xserver-xorg
```

---

### Post by Gotfredsen on 2007-11-10
Thanks for the help which cured my problem.

Got to get used to:

sudo -dtphsgtu update- nokjy- XXX123 - pq -install - update -uninstall -reconfug -help

stuf !!!

:)

/ Lars

---

