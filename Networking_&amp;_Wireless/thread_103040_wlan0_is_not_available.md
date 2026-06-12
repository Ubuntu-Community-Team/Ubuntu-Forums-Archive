---
title: "wlan0 is not available"
date: 2005-12-13
forum: Networking &amp; Wireless
---

### Post by executer on 2005-12-13
I have a D-link DWL 520+ and my internet and wlan have been working just fine, until now. 

I followed this howto: [http://ubuntuforums.org/showthread.php?t=75378](http://ubuntuforums.org/showthread.php?t=75378)
to install my ATI drivers.

I did these 3 commands from terminal:

sudo apt-get remove xorg-driver-fglrx
sudo apt-get remove linux-restricted-modules-$(uname -r)
sudo dpkg-reconfigure xserver-xorg #Select the ATI driver

and then rebooted as said in the howto. When I got back my "wlan0"
was not available neither from network settings or from terminal.
When typing "sudo iwlist" it just tells me no wlan card is available.
Seems like my card drivers is uninstalled or something.

So my question is how to reinstall these drivers? I used the
drivers in ubuntu and havent done anything with them after
installation. Guess this is Ndiswrapper drivers?

---

### Post by carlosqueso on 2005-12-13
> sudo apt-get remove linux-restricted-modules-$(uname -r)  you probably removed your network card drivers when you did this.  I'd try installing the restricted-modules for your processor type.

---

### Post by executer on 2005-12-13
I did this command: sudo apt-get install linux-restricted-modules-$(uname -r)

and rebooted. Now everything seems to be in order. They should have
told this in the howto.

Thanks.

---

### Post by carlosqueso on 2005-12-13
I'm surprized they didn't, appearantly they don't use proprietary wireless drivers, or they use ndiswrapper like me.......

---

