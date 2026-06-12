---
title: "Legacy Driver Installed Not Nvidia-glx"
date: 2007-01-28
forum: Multimedia &amp; Video
---

### Post by andytof47 on 2007-01-28
Hi I have a Geforce 4 mx 440 

Just trying to install the driver for it following this

[http://doc.gwos.org/index.php/Latest_Nvidia_Edgy#METHOD_1](http://doc.gwos.org/index.php/Latest_Nvidia_Edgy#METHOD_1)

Anyway i try to install the driver with

sudo apt-get install nvidia-glx

and i get

Note, selecting nvidia-glx-legacy instead of nvidia-glx

I thought a geforce4 mx440 needed the standard driver not the legacy????????

Why is this happening????

then I try to do  the next step


sudo nvidia-xconfig --no-composite

And i get

sudo: nvidia-xconfig: command not found


Please can someone help

Oh BTW I am using edgy

---

### Post by andytof47 on 2007-01-28
Don't worry about it

My Repos were wrong - had the ebox repos enabled which was messing with my repos....anyway comenting them out worked a treat

all good now

---

