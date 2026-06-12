---
title: "nVidia 3d acceleration with startx and gdm"
date: 2007-01-18
forum: Multimedia &amp; Video
---

### Post by ischnura on 2007-01-18
*Ubuntu 6.10* with *GeForce2 MX/MX 400* using *nVidia driver 9631*.

I have installed the nVidia drivers with [Alberto Milone's]("http://albertomilone.com/nvidia_scripts1.html") Python scrip: [Envy]("http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.8.1-0ubuntu2_all.deb")...

...but do not get the 3d acceleration working after loading gdm or after booting up. In order to get 3d acceleration I have to:
[LIST]
[*]kill gdm:
[/LIST]
```
sudo /etc/init.d/gdm stop
```
[LIST]
[*]and make start X:
[/LIST]
```
startx
```
and only then, the 3d acceleration works.


If I start *gdm* instead of *startx*
```
sudo /etc/init.d/gdm start
```
the 3d acceleration doesn't work.

The output of *glxinfo* with *sudo /etc/init.d/gdm start*
[INDENT][I]direct rendering: No
server glx vendor string: SGI
server glx version string: 1.2
client glx vendor string: NVIDIA Corporation
client glx version string: 1.4[/I][/INDENT]

The output of *glxinfo* with *startx*
[INDENT][I]direct rendering: Yes
server glx vendor string: NVIDIA Corporation
server glx version string: 1.4
client glx vendor string: NVIDIA Corporation
client glx version string: 1.4[/I][/INDENT]

It seems that the *server glx* is configured differently with *startx* and with *gdm start*.

Is there a way of configuring gdm, so that it sets the server glx properties same as the with startx?

Any help/hint will be **highly appreciated**!!

Thanks!!

btw.
the *nvidia* module is already included in the in */etc/modules*
the */var/log/Xorg.0.log* does not show any change when using *gmd* or *startx*

---

### Post by ischnura on 2007-01-19
I manage to fix the problem.

The last two days I was playing with XGL and Compiz and changed the configuration of */etc/gdm/gdm.conf-custom*

It was just a matter of returning to the original configuration...

And now every thing works perfectly!!

Thank you Alberto for your great script [Envy]("http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.8.1-0ubuntu2_all.deb") !!

ischnura

---

