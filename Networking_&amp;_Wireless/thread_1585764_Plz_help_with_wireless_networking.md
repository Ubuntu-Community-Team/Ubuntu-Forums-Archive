---
title: "Plz help with wireless networking"
date: 2010-10-01
forum: Networking &amp; Wireless
---

### Post by roman248 on 2010-10-01
Hi,
I have installed ubuntu on my Dell for the first time, and had no problems until i stumbled upon my wireless connection, which was not working. I connect to the internet wirelessly through win7, but ubuntu is not letting me do that: When I first load it up, it says that my wireless connection is "disabled", then after i try disabling it and enabling it back, the status for my wireless connection says "device not ready". Through windows7 i browsed my two network adapters, "Dell Wireless 1397 WLAN mini-card", and "Realtek PCIe GBE Family Controller", tried updating both of them, but the problem in ubuntu remains. Please help.

-Thanks

---

### Post by JBAlaska on 2010-10-01
Put the Ubuntu LiveCD in your drive and go to: **System, Administration, Software sources** and check the box below "Installable from CDROM". Then open a term and do:
```
sudo apt-get update

```
Then:
```
sudo apt-get install bcmwl-kernel-source
```

Now reboot and select the Broadcom STA driver. in **System, Administration, Hardware Drivers** Reboot again and you should have wireless.

---

### Post by roman248 on 2010-10-01
Thank you for  helping me. I used my USB stick to install ubuntu, so i dont have the LiveCD.. what should i do?

---

### Post by JBAlaska on 2010-10-01
If you can hook up a temporary Ethernet connection, you can install **bcmwl-kernel-source** that way.

---

### Post by roman248 on 2010-10-01
When I put in the 
```
sudo apt-get install bcmwl-kernel-source
```
It gives me:
```
roman@roman-laptop:~$ sudo apt-get install bcmwl-kernel-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  dkms fakeroot patch
Suggested packages:
  diffutils-doc
The following NEW packages will be installed:
  bcmwl-kernel-source dkms fakeroot patch
0 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/1,205kB of archives.
After this operation, 3,764kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Media change: please insert the disc labeled
 'Ubuntu 10.04.1 LTS _Lucid Lynx_ - Release i386 (20100816.1)'
in the drive '/cdrom/' and press enter
```
What am I doing wrong? Does this mean I still need the disk?

---

### Post by JBAlaska on 2010-10-01
As long as you have a Internet connection you will not need the LiveCD.

Go to **System, Administration, Software sources** and [COLOR="Red"]un-check[/COLOR] the box below "Installable from CDROM"

Then do:
```
sudo apt-get update
```

Then:
```
sudo apt-get install bcmwl-kernel-source
```

Reboot, then choose the Broadcom STA driver in **System, Administration, Hardware Drivers** Reboot again and you should have wireless.

---

### Post by roman248 on 2010-10-01
Oh! "UN-check". Darn my inattentiveness. Thank you very much sir, it works good now.

---

### Post by JBAlaska on 2010-10-01
Glad I could help. Enjoy Ubuntu Linux!

---

