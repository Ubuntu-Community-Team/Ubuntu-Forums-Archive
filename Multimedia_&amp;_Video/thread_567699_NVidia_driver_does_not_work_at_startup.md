---
title: "NVidia driver does not work at startup"
date: 2007-10-04
forum: Multimedia &amp; Video
---

### Post by posdnuos on 2007-10-04
I've installed the latest Nvdia driver via the install script I downloaded from Nvidia's website.  I manually edited my xorg.conf file to use the Nvidia driver.  The driver will not load at startup.

It will load right after I run the install script, though.  I started my computer, got an X error message, then manually installed the driver again.  I was able to start the X server this way.  I did not change the xorg.conf file the second time.

What's up?

---

### Post by 5-HT on 2007-10-04
The module usually loads automagically when called. When you refer to installing the module, do you mean compiling it and placing it in /lib/modules/... or just placing the module in the appropriate /lib/modules...?When you bootup and the module doesn't load, does manually loading it take care of the problem? If so, just append 'nvidia' to /etc/modules and it'll be loaded on boot.
cheers,

---

### Post by RomeReactor on 2007-10-04
Hi. Also make sure you're running the script with administrator privileges by using **sudo**:
```
sudo sh DRVERNAME.run
```
For example, to install the 64-bit driver on my system, I would enter:
```
sudo sh NVIDIA-Linux-x86_64-100.14.19-pkg2.run
```

---

### Post by posdnuos on 2007-10-04
> **5-HT said:**
> The module usually loads automagically when called. When you refer to installing the module, do you mean compiling it and placing it in /lib/modules/... or just placing the module in the appropriate /lib/modules...?When you bootup and the module doesn't load, does manually loading it take care of the problem? If so, just append 'nvidia' to /etc/modules and it'll be loaded on boot.
cheers,

The Nvidia installation script does not automatically install an Nvidia module for my setup.  I have to compile one every time I bootup.  After I do this the module will load.

I have an nvidia entry in my /etc/modules file, and it still doesn't work.  I've downloaded the file again, in case it was corrupted. 

To make it short:

--*bootup*
--*get x error: can't load Nvidia driver* 
sudo ./NVIDIA-Linux-x86-100.14.19-pkg1.run
--*compile new driver*
sudo pkill -HUP gdm
--*x window server starts successfully*

Thanks for your help!

---

