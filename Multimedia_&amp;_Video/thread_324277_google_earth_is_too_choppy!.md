---
title: "google earth is too choppy!"
date: 2006-12-23
forum: Multimedia &amp; Video
---

### Post by xpan on 2006-12-23
Hi,

I just installed google earth successfully but it is way too choppy. 

I use an ATI mobility Radeon X700 PCIX w/ 128MB Ram on my laptop. 

Any ideas on how to improve the performance? 

PS: glxgears runs smoothly even in full screen

---

### Post by Hendrixski on 2006-12-23
are you sure you have the ATI driver installed properly?

Google earth was choppy for me too, then I got the binary driver, now it's smooth

---

### Post by xpan on 2006-12-23
I didn't install any ATI driver. I use the ATI driver installed along with UBUNTU. I checked the xorg.conf and it displays the correct information about my card.

How can I know if it is installed correctly?

---

### Post by taurus on 2006-12-23
[http://albertomilone.com/driver_edgy.html](http://albertomilone.com/driver_edgy.html)

---

### Post by xpan on 2006-12-24
thanks, 

alternatively can I download from here: [http://ati.amd.com/support/drivers/linux/linux-radeon.html](http://ati.amd.com/support/drivers/linux/linux-radeon.html)

and in someway transform .rpm to .deb?

---

### Post by tseliot on 2006-12-24
> **xpan said:**
> thanks, 

alternatively can I download from here: [http://ati.amd.com/support/drivers/linux/linux-radeon.html](http://ati.amd.com/support/drivers/linux/linux-radeon.html)

and in someway transform .rpm to .deb?

No, you shouldn't do that. Those rpms are not compiled with the support for Ubuntu's Xorg version. You might use the installer and generate deb packages if you like

---

### Post by xpan on 2007-01-04
Hi, its me again.

I followed your guide to install ATI drivers (I use a mobile radeon X700 PCI-X card) but now whenever I choose a 3D screen saver to check the speed of 3D graphics, I get my X server restarted when I try to close the screen saver preview. 

I had installed the binary ATI driver using synaptics package manager so I had to do this:
> 
sudo aptitude update && sudo aptitude dist-upgrade


But I get this:

> 
ignore [http://www.albertomilone.com](http://www.albertomilone.com) binary/ Release.gpg
ignore [http://www.albertomilone.com](http://www.albertomilone.com) binary/ Translation-el
ignore [http://www.albertomilone.com](http://www.albertomilone.com) binary/ Release
ignore [http://www.albertomilone.com](http://www.albertomilone.com) binary/ Packages
ignore [http://www.albertomilone.com](http://www.albertomilone.com) binary/ Packages
  404 Not Found


I also checked the 
/etc/default/linux-restricted-modules-common

and this is what I see: DISABLED_MODULES= ""

any ideas what might be the cause? 

PS: I also cannot run GoogleEarth anymore.

---

