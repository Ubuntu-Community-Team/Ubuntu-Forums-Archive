---
title: "Beta NVidia driver fails after reboot [SOLVED]"
date: 2006-11-06
forum: Multimedia &amp; Video
---

### Post by Masuran on 2006-11-06
Hello everyone,

I have a wierd problem with the Beta Nvidia driver on Ubuntu Edgy I install it from the official nvidia installer, just sudo sh NVidia*.run (don't have the full filename here) and everything works perfectly. Even Beryl is as smooth as ice :)

But when I reboot my system Xorg complains that the NVidia drivers is a different version and I have to reïnstall the driver (compile again and such), then everything is back ok.... Until my next reboot :(

Anyone got a clue?

PROBLEM SOLVED
Sorry for posting to fast :) 
The answer was disabling the nv module by adding this the file **/etc/default/linux-restricted-modules-common** file

***DISABLED_MODULES="nv"***

---

### Post by smartbei on 2006-12-06
I used a similar solution. Adding 'nv' didn't solve the problem - it didnt change a thing. I did: 
```
DISABLED_MODULES="nv nvidia"
```
Just nvidia might work also, I am just not feeling like rebooting yet again...have done so many, many times in the last hour.

---

