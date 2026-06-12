---
title: "No sound in Ubuntu with asus lamborghini"
date: 2009-03-17
forum: Multimedia Software
---

### Post by tjajab on 2009-03-17
Just wanted to share a success story, if anyone else but me have had the same problems.

When I upgraded to Intrepid Ibex, I lost my sound. I have a Asus Lamborghini VX2 and it felt like I have tried all the troubleshooting guides on the Internet :)

My aplay -l listed AD198x, so I did not now what exact model my machine was using. However, somewhere I found the command
```
tail /proc/asound/oss/sndstat
```
which told me I had a AD1986A.

From now on it was easier. Looking at the list in /usr/share/doc/alsa-base/driver/ALSA-Configuration.txt.gz I found that I could try adding
```
options snd-hda-intel model=laptop
```
to the file /etc/modprobe.d/alsa-base

Somewhere I read the wrong syntax (options snd-hda-intel laptop) without the model= and that confused me quite a bit. When I rebooted, it worked!

edit: you may have to install the newest alsa drivers as described here: [http://ubuntuforums.org/showthread.php?p=6589810#post6589810](http://ubuntuforums.org/showthread.php?p=6589810#post6589810)

---

### Post by bertolo on 2009-04-06
try this:
open volume control, preferences, enable all the xit there. put volume in max in all parameters.
then in switches choose headphones and disable the other two options below.
ps:select HDA intel drivers.
this was my solution when i had the same problem

---

