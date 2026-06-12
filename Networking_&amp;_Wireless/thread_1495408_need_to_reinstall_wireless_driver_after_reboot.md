---
title: "need to reinstall wireless driver after reboot"
date: 2010-05-28
forum: Networking &amp; Wireless
---

### Post by pinker on 2010-05-28
Hi,

ive been searching forums like for 2 days, but couldnt find any similar problem.
First of all im running Ubuntu 10.04 desktop version on my netbook Acer aspire one (AOD150)
Every time i turn off my netbook and after turn it on, in "Hardware drivers" it says that driver for wifi is not in use, also button for swithing on/off wifi is not working. 
So everytime i start up i have to go into "Hardware drivers", remove driver for wifi, and then activate it again. And everything is working gr8 after. Its just too annoying to do it everytime.

---

### Post by pinker on 2010-05-29
bumb,

i bet there must be some solution for this ...

---

### Post by qwerty2009 on 2010-05-29
Have you tried installing the back-ported wireless modules? copy and paste the following into terminal...
> sudo apt-get install linux-backports-modules-wireless-2.6.32-22-generic

---

### Post by pinker on 2010-05-29
Nope didnt work, when i installed it i rebooted my netbook.
After boot wifi was still not recognized, so i went to Hardware drivers and needed to remove and activate it again, but now for change it was still not working and it said that i need to restart.
So i did but after boot same again, not recognized.
So i had to remove those backport modules to get connected again.

---

### Post by senormoll on 2010-06-19
I have the EXACT same problem.  And the weird thing is, I bought my brother and my mom the exact same laptops and both are running the exact same version of Ubuntu.  The only difference, not that it matters, is that my mom's laptop has win7 on it too.  This is the kind of stuff that Ubuntu does that just makes me crazy :confused:

---

### Post by iamnotanexpert on 2012-01-01
Hello, i met the same issue with the last 11.10 Oneiric Ocelot release.

To solve it i followed these procedure:

sudo ndiswrapper -i ~/drivers/drivername.inf  (to install the driver).
sudo depmod -a
sudo modprobe ndiswrapper (to etablish the wireless connection for the current session)
echo "ndiswrapper" | sudo tee -a /etc/modules (to load the ndiswrapper module automatically after reboot).

---

