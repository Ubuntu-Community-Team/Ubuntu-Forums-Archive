---
title: "How to install Catalyst 9.1 on Ubuntu 8.10?"
date: 2009-02-05
forum: Multimedia Software
---

### Post by oblidor on 2009-02-05
Hi

I'm still using the Catalyst that came with Ubuntu 8.10, because last time I tried to install a newer version it all broke down.

Could somebody point to the best way of upgrading to 9.1 or better? I really want to get movies to work better with Compiz.

Thanks in advance

---

### Post by markbuntu on 2009-02-05
I have had success just downloading the driver from ati and running the installer for my HD3650 card. Others have not had such good luck. It seems to depend on what card you have.

Be sure to remove the old driver completely before installing the new one and make sure you have desktop visual effects(compiz) set to none before doing anything. This will help prevent bad things from happening if anything goes wrong.  Read the release notes and installer instructions.

Also, be sure to save the driver somewhere convenient because you will most likely need to rerun the installer after a kernel update.

---

### Post by ohgodnotanother1 on 2009-02-05
You can do it manually as it is described in the following wiki:
[http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide#Installing_the_restricted_drivers_manually](http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide#Installing_the_restricted_drivers_manually)

---

### Post by monikersupreme on 2009-02-07
Where can I get the 32bit version of this driver (or better yet, if I can get it as a .deb)?

If not... how do I install the (.run) driver downloaded from AMD? If I need to remove the old driver before installing the new one how do I do that... 

Will these drivers be available in the Ubuntu repository at some point?

---

### Post by ohgodnotanother1 on 2009-02-08
> **monikersupreme said:**
> Where can I get the 32bit version of this driver (or better yet, if I can get it as a .deb)?
You can get the driver from the ATI website: [http://ati.amd.com/support/driver.html](http://ati.amd.com/support/driver.html)
Select "Linux x86" from the first list, which contains the operating system. There is no .deb package supplied by ATI. You get it as a .run script.

> **monikersupreme said:**
> If not... how do I install the (.run) driver downloaded from AMD? If I need to remove the old driver before installing the new one how do I do that... 
You execute the .run script by setting its execution flag. Enter "chmod o+x ati-driver-installer-X-Y.run" for example. Then execute it from a terminal window.
Open "Application/System/Hardware Drivers" (this is for Xubuntu though) and make sure that the "Enabled" checkbox for your "ATI accelerated graphics driver" is not checked. If it is: uncheck. Install the driver after that.

> **monikersupreme said:**
> Will these drivers be available in the Ubuntu repository at some point?
Definitely not, because these are proprietary drivers which are closed source. Ubuntu repositories only contain open source software.

---

### Post by Ubuntiac on 2009-02-08
> **ohgodnotanother1 said:**
> Definitely not, because these are proprietary drivers which are closed source. Ubuntu repositories only contain open source software.

Hmmm... Kind of accurate but misleading. Yes, they won't be in the *repositories* but that doesn't mean Ubuntu won't make them *available*. Eventually they'll just be available through the restricted driver manager / EnvyNG, just like the previous versions.

The open source drivers really are getting better rapidly though, so who knows, depending on what you need, by the time they're available maybe you won't need them. :)

---

### Post by Melcar on 2009-02-09
fglrx is available in the Ubuntu repositories.  What Ubuntu can't do, because the drivers are proprietary, is include them in the kernel.
Lastly, you can generate .deb packages of fglrx if you want.  The installer you get from ATI's website lets you do this ( --buildpkg). 

To install them is really easy.  First get the driver from ATI's website (the installer is for both 32bit and 64bit).  Then make sure you have all the dependencies (you probably already do, but doesn't hurt to check):

```
sudo apt-get install build-essential cdbs fakeroot dh-make debhelper debconf libstdc++5 dkms 

#install ia32-libs as well if you're using 64bit
```

Next move to the directory you installed the driver to:

```
cd <location of driver>
```

Now run the installer:

```
sudo sh ati*.run
```

Use the default options and let it finish.  When you get dropped back to the terminal make sure you did not get any errors, and then initialize the driver:

```
sudo aticonfig --initial
```

Reboot.

---

### Post by ohgodnotanother1 on 2009-02-09
Yes, that's all described step-by-step in the wiki I posted before:> **ohgodnotanother1 said:**
> You can do it manually as it is described in the following wiki:
[http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide#Installing_the_restricted_drivers_manually](http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide#Installing_the_restricted_drivers_manually)

---

