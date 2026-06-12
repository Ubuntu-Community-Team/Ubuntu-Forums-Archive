---
title: "dpkg-configure -r option problem"
date: 2008-06-29
forum: Multimedia Software
---

### Post by cotcot on 2008-06-29
My nvidia broke, so i had to fall back on the ATI Xpress 1250 of my motherboard. I am running it with the vesa driver for the moment.
I followed the official way to install fglrx ([[COLOR="Red"]see here[/COLOR]]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI")).
This is what it is instructing for hardy :
> Enable accelerated the accelerated ATI graphics driver in the restricted-manager, then do: {{{sudo dpkg-reconfigure -phigh linux-restricted-modules-uname -r sudo insmod /lib/modules/uname -r/volatile/fglrx.ko}}} Log out and log in. 
I got stuck on the instruction ```
sudo dpkg-reconfigure -phigh linux-restricted-modules-uname -r sudo insmod /lib/modules/uname -r/volatile/fglrx.ko
```
The "-r" option is not known. I have checked it in the man-page as well.

Can anybody put some light on this ?

Thanks

---

### Post by syczu on 2008-06-29
-r is remove, try --remove or --purge

---

### Post by cotcot on 2008-06-29
SOLVED
I had to specify the kernel number (output of 'uname -r' in terminal); and the second sudo is a separate instruction ; so i added &&

> sudo dpkg-reconfigure -phigh linux-restricted-modules-[COLOR="Red"]uname -r[/COLOR] sudo insmod /lib/modules/[COLOR="Red"]uname -r[/COLOR]/volatile/fglrx.ko

> sudo dpkg-reconfigure -phigh linux-restricted-modules-[COLOR="Red"]2.6.24-19-generic[/COLOR] && sudo insmod /lib/modules/[COLOR="Red"]2.6.24-19-generic[/COLOR]/volatile/fglrx.ko

The official instruction could be better like this 
> sudo dpkg-reconfigure -phigh linux-restricted-modules-[COLOR="Red"]'uname -r'[/COLOR] && sudo insmod /lib/modules/[COLOR="Red"]'uname -r'[/COLOR]/volatile/fglrx.ko where you replace 'uname -r' with your output of ```
uname -r
```

---

### Post by cotcot on 2008-06-29
I took incomplete information from the official documentation because there were syntax errors in (html code).
I have corrected them in launchpad.

---

