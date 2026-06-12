---
title: "nvidia-settings refuses to acknowledge nvidia driver"
date: 2007-10-28
forum: Multimedia &amp; Video
---

### Post by relix on 2007-10-28
So I switched from an Ati card to an Nvidia card.

Installed the restricted drivers using the manager in Gutsy, had some troubles (had to dpkg-divert --remove two symlinks generated but not cleaned by fglrx) but in the end it worked out. I used nvidia-xconfig to initalize a new xorg.conf.

Now apparantly everything is ok. in Xorg.conf "Driver nvidia" is there instead of nv, and I can get the effects (compiz?) to work. One problem though - I'm not getting dual screens. I read somewhere you can use nvidia-settings to set this up, so I tried that. This continually gives me the following error, though:

You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. 

But no matter how much I do nvidia-xconfig, it keeps on telling me the above error. It's also not showing any options other than some general settings like "ask me to quit when quitting".

Anyone know what's up?

---

### Post by Stinger on 2007-10-30
Hi , nvidia-settings must be run as su (root) maybe thats your trouble ? the same goes for nvidia-xconfig
In a terminal do:
```
sudo nvidia-settings
```
or
```
sudo nvidia-xconfig
```

It worked for my monitor , couldn't get the new screenconfigtool to work with the nvidia driver, the refresh rates were much to low , but with nvidia-settings it worked fine , no flickering picture anymore.
Haven't got two monitors yet though.

---

### Post by relix on 2007-10-30
Sorry, I already was executing them as root. :(

---

### Post by dabl on 2007-10-30
My experience with the Restricted Driver Manager in Gutsy has been less than satisfactory -- I recommend using Envy to install the correct Nvidia driver on your system.  Download the file:

"envy_0.9.8-0ubuntu10_all.deb"

from this web site:

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

and just right-click it and choose "Open with > Gdebi" (or something similar). When it is installed, it will put an icon in your System folder.  You can also run it from the console with ```
sudo envy -t
``` which is very handy when you accept a kernel upgrade and lose your GUI.  :guitar:

---

