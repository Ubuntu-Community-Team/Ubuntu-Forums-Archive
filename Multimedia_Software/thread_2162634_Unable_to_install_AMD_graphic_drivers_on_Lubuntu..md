---
title: "Unable to install AMD graphic drivers on Lubuntu."
date: 2013-07-15
forum: Multimedia Software
---

### Post by Maikiro on 2013-07-15
I get this error when trying to install AMD Graphic Drivers.

Check if system has the tools required for installation.
fglrx installation requires that the system have kernel headers.  /lib/modules/3.8.0-26-generic/build/include/linux/version.h cannot be found on this system.
One or more tools required for installation cannot be found on the system. Install the required tools before installing the fglrx driver.
Optionally, run the installer with --force option to install without the tools.
Forcing install will disable AMD hardware acceleration and may make your system unstable. Not recommended.


Anyone advise as no idea what to do.

Thanks

Maikiro

---

### Post by Cheesemill on 2013-07-15
It looks like you don't have the kernel headers installed. You can install them by doing...
```
sudo apt-get install linux-headers-$(uname -r)
```

Is there any reason you are trying to install the drivers from the AMD website instead of using the 'Additional Drivers' application that is part of Lubuntu?
Usually this will automatically detect and install the latest compatible drivers for your system.

Also which version of Lubuntu are you using and which graphics chip does your machine have? It may be the case that there aren't any drivers available for your particular combination.

---

### Post by Maikiro on 2013-07-15
Running Lbuntu 13.04.
AMD Radeon HD 2400
Dont have Additional Drivers App anywhere.

Also once done the command you have given me I get: 

Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-3.8.0-26-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by QIII on 2013-07-15
Hello.

Unfortunately, AMD/ATI has stopped development of the 2xxx - 4xxx series drivers.  Since the legacy driver will not work with the version of X Server in 13.04 it would be best to use the open source Radeon driver that was installed by default.

I would highly recommend against any of the hack methods that might be suggested for getting your card to work with the legacy driver.  Those methods effectively break your installation.

Best wishes!

---

### Post by Cheesemill on 2013-07-15
You are already using the only available drivers for your system.

ATI dropped support for all of the 2/3/4xxx series cards over a year ago so no drivers exist for your card for versions of Lubuntu later than 12.04.

---

