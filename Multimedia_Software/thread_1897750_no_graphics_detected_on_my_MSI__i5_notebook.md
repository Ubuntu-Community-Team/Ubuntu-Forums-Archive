---
title: "no graphics detected on my MSI  i5 notebook"
date: 2011-12-19
forum: Multimedia Software
---

### Post by johndlz on 2011-12-19
I have an MSI notebook with intel GMA HD its a shared graphics.. now my problem is when i check additional software so that i can install the driver. unfortunately theres no driver found, can somebody who  has an idea about this, please share your idea to me, i want to try some 3d thng on ubuntu,

thanks,

---

### Post by BicyclerBoy on 2011-12-19
The correct driver for all intel GPU is free open source & included with ubuntu..

It may not be configured completely because the std ubuntu version is dated..
 
To check setup in a terminal:
glxinfo | grep OpenGL
glxgears

cat /var/log/Xorg.0.log | grep i915
cat /var/log/Xorg.0.log | grep DRI
cat /var/log/Xorg.0.log | grep WW

---

### Post by inobe on 2011-12-19
can anyone confirm using x-swat updates ppa will provide the best intel driver and tools?

[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

i don't see much using filter for oneric 11.10!

---

### Post by johndlz on 2011-12-20
[BicyclerBoy]("http://ubuntuforums.org/member.php?u=816321") is there any way I can install the driver?

---

### Post by 2F4U on 2011-12-20
What driver are you looking for? As already said before, Intel drivers are already included in a default install. You can't install them through Additional Drivers, since that is only for proprietary drivers. Intel drivers are open source and hence included by default.
I can't see from your initial post that there are any problems with the currently installed drivers, so why would you want to install other drivers?

---

