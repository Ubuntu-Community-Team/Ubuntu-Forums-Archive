---
title: "b43 error natty 11.04"
date: 2011-08-22
forum: Networking &amp; Wireless
---

### Post by unknow04 on 2011-08-22
hi guys! i have a problem, I have install the broadcom sta wireless driver on my laptop it works fine but i guess it's not compatible with aircrack cause i cant scan using the wepcrackgui. So I try install b43 driver but I always have the same error  when I type on the termial 

sudo apt-get install b43-fwcutter firmware-b43-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libgdata1.7-cil libmono-zeroconf1.0-cil libgkeyfile1.0-cil
  libubuntuone1.0-cil libgtk-sharp-beans-cil libtaglib2.0-cil libgudev1.0-cil
  libnotify0.4-cil
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  b43-fwcutter firmware-b43-installer
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/18.2 kB of archives.
After this operation, 131 kB of additional disk space will be used.
Selecting previously deselected package b43-fwcutter.
(Reading database ... 167567 files and directories currently installed.)
Unpacking b43-fwcutter (from .../b43-fwcutter_1%3a013-3_i386.deb) ...
Selecting previously deselected package firmware-b43-installer.
Unpacking firmware-b43-installer (from .../firmware-b43-installer_4.150.10.5-5_all.deb) ...
Processing triggers for man-db ...
Setting up b43-fwcutter (1:013-3) ...
Setting up firmware-b43-installer (4.150.10.5-5) ...
Not supported low-power chip with PCI id 14e4:4315!
Aborting.
dpkg: error processing firmware-b43-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 firmware-b43-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)
 
anyone know what is going on ? 
Im using Ubuntu natty 11.04

---

### Post by nm_geo on 2011-08-22
you have the low power chip.

> Not supported[COLOR=Red] low-power chip[/COLOR] with PCI id 14e4:4315!

need the low power firmware

```
sudo apt-get install firmware-b43-lpphy-installer
```

---

### Post by unknow04 on 2011-08-23
thanks a lot for your quick answer. But after installing that the b43 driver will work right ?

---

### Post by lkjoel on 2011-08-23
It might work or it might not. You'll have to reboot after installing the firmware that nm_geo suggested.

---

### Post by unknow04 on 2011-08-23
it works!!! thanks a lot mm_geo you a re a genius and thanks for your answer too lkjoel

---

### Post by nm_geo on 2011-08-23
> **unknow04 said:**
> it works!!! thanks a lot mm_geo you a re a genius and thanks for your answer too lkjoel
 
Not really a genius.  I have just seen this problem before ... Enjoy ..

---

