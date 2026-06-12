---
title: "lousy projectm performance with Radeon HD 5700"
date: 2011-05-29
forum: Multimedia Software
---

### Post by korgoth28 on 2011-05-29
I built a new computer a while back with a phenom II 3.2 ghz (unlocked to 4 stable cores :cool:) and a Radeon HD 5700 Series (I think this one: [http://www.amazon.com/Sapphire-Radeon-DisplayPort-PCI-Express-100283-3L/dp/B0035K6H2C](http://www.amazon.com/Sapphire-Radeon-DisplayPort-PCI-Express-100283-3L/dp/B0035K6H2C)).

In theory this system should be able to crank up the settings pretty high, right? With nothing else running but youtube in iceweasal, it can barely handle 512 megabyte textures and all the other settings pretty low. If I make the window much larger than the default 512x512 the framerate crashes, and that's a pretty small window (my resolution is 1400x900).  In the past, with much worse systems, I could turn the mesh down to 64 and fullscreen would go smoothly, though it would be unwatchably ugly. Now it's unwatchably ugly AND the framerate doesn't seem to be much better.

Install of projectm was extremely smooth.

I vaguely remember installing disabling and installing drivers manually a while back (I started with a pretty minimal install). But I thought I got it so it was using the driver offered by ATI without being slowed down by ndiswrapper. Could the driver be the issue?

Any other ideas?

Thanks!

---

### Post by Yellow Pasque on 2011-05-29
What version of Ubuntu are you using? Also, post output of:
```
fglrxinfo
```
EDIT: BTW, ndiswrapper is a tool for using Windows wireless drivers

---

### Post by korgoth28 on 2011-05-29
I'm using 11.10.

It probably wasn't NDISwrapper I'm thinking of. I was trying to get wireless cards to work at the same time so I'm probably getting them confused.

Also:

> root@localhost:~# fglrxinfo
bash: fglrxinfo: command not foundI take it that would be a good thing to install?

EDIT: istalled a bunch of packages with fglrx in them and now it says:

> root@localhost:/home/mike# fglrxinfo
Segmentation fault

---

### Post by Yellow Pasque on 2011-05-29
I'm not sure if fglrx installs on 11.10 yet :\ Post output of:
```
glxinfo
```

---

### Post by korgoth28 on 2011-05-29
Still "command not found".

---

### Post by Yellow Pasque on 2011-05-29
> $ glxinfo
The program 'glxinfo' is currently not installed.  You can install it by typing:
sudo apt-get install mesa-utils
...

---

### Post by mockingbird on 2011-05-29
Are you using Gallium or Catalyst?

---

