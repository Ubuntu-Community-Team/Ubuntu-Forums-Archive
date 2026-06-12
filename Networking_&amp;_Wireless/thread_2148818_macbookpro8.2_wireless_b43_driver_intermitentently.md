---
title: "macbookpro8.2 wireless b43 driver intermitentently losing internet access"
date: 2013-05-26
forum: Networking &amp; Wireless
---

### Post by miguelnegrao on 2013-05-26
Hi

I have a macbookpro8,2 and I'm running the b43 driver for wireless. I never loose the wireless connection but every couple of minutes I can't send or receive any data, I can't ping any machine. disconnecting from the wireless and reconnecting gets the internet access working again. I think the b43 driver might be misbehaving... anyway to troubleshoot  this ?

best,
Miguel Negrão

---

### Post by Hadaka on 2013-05-26
Hi Miguel, and welcome.
 when you loaded the wifi driver did you use this command?
```
sudo apt-get install b43-fwcutter firmware-b43-installer 
```
or something different.
please Copy and paste this command.
```
lspci -nn | egrep '0200|0280'
```
post the output..
thanks.

---

### Post by miguelnegrao on 2013-05-27
Hi Hadaka,

> **Hadaka said:**
> Hi Miguel, and welcome.
 when you loaded the wifi driver did you use this command?
```
sudo apt-get install b43-fwcutter firmware-b43-installer 
```
or something different.
please Copy and paste this command.
```
lspci -nn | egrep '0200|0280'
```
post the output..
thanks.

Yes, they are installed:
```

miguel@miguel-MacBookPro:~$ dpkg -l | grep b43
ii  b43-fwcutter                                   1:015-14                                   amd64        Utility for extracting Broadcom 43xx firmware
ii  firmware-b43-installer                         1:015-14                                   all          Installer package for firmware for the b43 drive

```

but in [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43%20-%20Internet%20access](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43%20-%20Internet%20access) it says:

> 
**Note:** Since 11.10 the package linux-firmware-nonfree also contains b43 firmware ([changelog]("https://launchpad.net/ubuntu/oneiric/+source/linux-firmware-nonfree/+changelog")).  This may contain a different/newer version of the firmware depending on release.


So, do we still need b43-fwcutter and firmware-b43-installer ? I do have linux-firmware-nonfree installed.

```

miguel@miguel-MacBookPro:~$ lspci -nn | egrep '0200|0280'
02:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM57765 Gigabit Ethernet PCIe [14e4:16b4] (rev 10)
03:00.0 Network controller [0280]: Broadcom Corporation BCM4331 802.11a/b/g/n [14e4:4331] (rev 02)

```

Miguel

---

### Post by Hadaka on 2013-05-27
Hi, your card runs best on the linux-firmware-nonfree.
from a wired connection please do...
```
sudo apt-get remove --purge b43-fwcutter firmware-b43-installer
 sudo apt-get install --reinstall linux-firmware-nonfree
```
also check that your router settings are not tkip
and if possible the prefered wpa2. You might also want to look
at the channel concentration in your area and change channel
if needed.

---

