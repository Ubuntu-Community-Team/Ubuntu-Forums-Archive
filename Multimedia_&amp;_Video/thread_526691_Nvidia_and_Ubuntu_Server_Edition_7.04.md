---
title: "Nvidia and Ubuntu Server Edition 7.04"
date: 2007-08-15
forum: Multimedia &amp; Video
---

### Post by infinitezero on 2007-08-15
I was unable to install Nvidia on the 7.04 server edition and and wondering if anyone had any thoughts?

I have tried every method on the forum and even the auto install by tseliot. I have been a Linux user for a while now and never have I had video driver kick my back side so badly, any help would be greatly appreciated.  

Thanks,
iz

---

### Post by infinitezero on 2007-08-15
Anyone have any ideas on this one?


Thanks,
iz

---

### Post by RomeReactor on 2007-08-15
Hi. I don't know much about servers, but if I'm not mistaken the default install is CLI, correct? so I assume you have now added Gnome, KDE, XFCE or another desktop environment. What specific model of nVidia card do you have? if it's installed now, try this:
```
sudo lshw -C display
```
to see details about the card. Have you installed the **nv** driver first?
```
sudo apt-get install xserver-xorg-video-nv
```
Hopefully someone more knowledgeable will show up and provide you with a relevant answer. You could also search and/or post in the [Servers & Security]("http://ubuntuforums.org/forumdisplay.php?f=7") section.

---

### Post by tseliot on 2007-08-16
> **infinitezero said:**
> I was unable to install Nvidia on the 7.04 server edition and and wondering if anyone had any thoughts?

I have tried every method on the forum and even the auto install by tseliot. I have been a Linux user for a while now and never have I had video driver kick my back side so badly, any help would be greatly appreciated.  

Thanks,
iz

Can  you tell us exactly what happened?

For example you could post your /var/log/envy-installer.log if you haven't uninstalle Envy yet

---

### Post by infinitezero on 2007-08-23
tseliot, 
I have already un-installed Envy.

Which ever method I use produces the same result, X-server will not start after reboot.

---

