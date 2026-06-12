---
title: "Ethernet: Anyone really having the file  &quot;b43/ucode15.fw&quot;"
date: 2011-08-21
forum: Networking &amp; Wireless
---

### Post by honeybear on 2011-08-21
Hi,

This file shall exist somewhere.Ok broadband can be installed, but at least one person in the world has it.

Please this person post us a LINK ;) 

Thank you so much

---

### Post by praseodym on 2011-08-21
Do you have a wired connection:

until 10.10:

```
sudo apt-get install --reinstall b43-fwcutter
```

for 11.04:

```
sudo apt-get install --reinstall b43-fwcutter firmware-b43-installer
```
Without connection, download the attached file and unpack it to /lib/firmware:

```
sudo tar xvf Broadcom_Firmware.tar.gz -C /lib/firmware/ 
```
and reboot.

---

### Post by blade4 on 2011-08-21
The b43-fwcutter deb file can also be found in the pool/main/b folder of the LiveCD or LiveUSB .

---

### Post by honeybear on 2011-08-21
> **praseodym said:**
> Do you have a wired connection:

until 10.10:

```
sudo apt-get install --reinstall b43-fwcutter
```

for 11.04:

```
sudo apt-get install --reinstall b43-fwcutter firmware-b43-installer
```
Without connection, download the attached file and unpack it to /lib/firmware:

```
sudo tar xvf Broadcom_Firmware.tar.gz -C /lib/firmware/ 
```
and reboot.


Man, I googled for those files during 1 or 2 days ... 
Wow all those files !! thank you so much !!!

---

### Post by gardiary on 2012-10-05
Thanks a lot for the files.. its works !

---

