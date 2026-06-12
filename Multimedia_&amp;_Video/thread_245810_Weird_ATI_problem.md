---
title: "Weird ATI problem"
date: 2006-08-28
forum: Multimedia &amp; Video
---

### Post by SteinbergerNate on 2006-08-28
Well, I got my ATI drivers working and all. fglrxinfo gives me the correct information and glxgears runs very smoothly (1400 fps). Any opengl games I have run well. 

However, when I use an opengl screensaver, they are VERY jerky. This isn't a huge issue since screensavers aren't all that important but I would like to have everything working as it was intended.

---

### Post by SteinbergerNate on 2006-08-30
Bump.

---

### Post by awry on 2006-09-08
I have the same problem.  T60p laptop with the FireGL V5200.  Seems like gnome-screensaver isn't using fglrx for some reason.

---

### Post by Tingvan on 2006-09-09
maybe your ati's 3D acceleration doesnt work.
please type:
> 
$ fglrxinfo
display: :0.0 screen: 0
OpenGL vendor string: Mesa project:[www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)

if yours is same to the above.
you should download the ati driver from the ati website and install it.
like this:
> 
sudo module-assistant prepare
sudo ./ati***.run (the driver you download from the ati website&#65289;

finish your install and then reboot
and check the fglrxinfo again.

---

