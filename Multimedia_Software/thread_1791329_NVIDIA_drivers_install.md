---
title: "NVIDIA drivers install"
date: 2011-06-26
forum: Multimedia Software
---

### Post by mamboknave on 2011-06-26
If I have to pick the single most frustrating and persistent issue in Ubuntu always and ever, is the installation of Nvidia drivers.

After a couple of hours of trials & errors, I ~might~ have (successfully?) installed the new 275.09.07 on Ubuntu 10.04.

But I had to add to /etc/modprobe.d/blacklist.conf the five items described in [http://ubuntuforums.org/showthread.php?t=1467074](http://ubuntuforums.org/showthread.php?t=1467074)

Now, the "NVIDIA X Server Setting" tab shows me the 275.09.07 as installed and functioning.

BUT, here is the problem:
the "Hardware Drivers" tab tells that "No proprietary drivers are in use on this system".

So, what's going on? How do I know which driver is being used now?

Thanks for reading and... replying.

---

### Post by beew on 2011-06-26
Yeah, why do you want to install the driver manually and then complain about it? If you don't want frustrations use the automatic tool. Click "Additional Drivers" and let it detect and install the driver for you. Then add the ppa [https://launchpad.net/~ubuntu-x-swat/+archive/x-updates]("https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates") and update if you want a more up to date version.

---

