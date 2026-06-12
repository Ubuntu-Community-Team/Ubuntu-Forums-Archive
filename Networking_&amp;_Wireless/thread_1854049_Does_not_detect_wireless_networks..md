---
title: "Does not detect wireless networks."
date: 2011-10-03
forum: Networking &amp; Wireless
---

### Post by iNeeed on 2011-10-03
Hello Ubuntu's

I recently installed 11.04 and now my wireless is not detecting any networks.  It was working fine in my previous version of ubuntu.  I am using a Dell Inspiron 6400 Laptop 
I imagine it is something with my wirelss driver. It says it is activated but I can not see any networks.  
Any help greatly appreciated! 

It says I have Broadcom STA Wireless driver and it is activated.
This package contains Broadcom 802.11 Linux STA wireless driverfor use with Broadcom's BCM4311-, BCM4312-, BCM4313-, BCM4321-,BCM4322-, BCM43224-, and BCM43225-, BCM43227- and BCM43228-basedhardware.

---

### Post by westie457 on 2011-10-03
> **iNeeed said:**
> Hello Ubuntu's

I recently installed 11.04 and now my wireless is not detecting any networks.  It was working fine in my previous version of ubuntu.  I am using a Dell Inspiron 6400 Laptop 
I imagine it is something with my wirelss driver. It says it is activated but I can not see any networks.  
Any help greatly appreciated! 

It says I have Broadcom STA Wireless driver and it is activated.
This package contains Broadcom 802.11 Linux STA wireless driverfor use with Broadcom's BCM4311-, BCM4312-, BCM4313-, BCM4321-,BCM4322-, BCM43224-, and BCM43225-, BCM43227- and BCM43228-basedhardware.

Hi open a terminal type in ```
lspci -vnn
``` What does that tell us please.

Thank you.

---

### Post by pdc on 2011-10-03
this seems like a middle-aged laptop

if like others it should say

> description: Network controller
       product: BCM4311 802.11b/g WLAN

and 

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

this would seem to suggest sta

---

### Post by bkratz on 2011-10-03
If it is indeed a BCM4311 here is the best description of it use in 11.04.

[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_Natty_11.04](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_Natty_11.04)

---

### Post by pdc on 2011-10-03
thanks

---

### Post by iNeeed on 2011-10-04
Thanks people.  Evidently I had 2 almost identical posts in 2 places and did not see your responses.  I think they would have helped.  This is what I did and it is working now.  

    Removed the Broadcom STA wireless Driver from Additional Drivers.
    type bcm in Ubuntu software center,
    Install "Installer Package for firmware for the b34 driver" (firmware-b43-installer)


Via  [http://askubuntu.com/questions/38327/broadcom-bcm4311-wireless-not-working](http://askubuntu.com/questions/38327/broadcom-bcm4311-wireless-not-working)

Thanks!

---

### Post by bkratz on 2011-10-04
> **iNeeed said:**
> Thanks people.  Evidently I had 2 almost identical posts in 2 places and did not see your responses.  I think they would have helped.  This is what I did and it is working now.  

    Removed the Broadcom STA wireless Driver from Additional Drivers.
    type bcm in Ubuntu software center,
    Install "Installer Package for firmware for the b34 driver" (firmware-b43-installer)


Via  [http://askubuntu.com/questions/38327/broadcom-bcm4311-wireless-not-working](http://askubuntu.com/questions/38327/broadcom-bcm4311-wireless-not-working)

Thanks!


We are all just glad you got it working, congratulations!

---

### Post by westie457 on 2011-10-04
Glad its working. Could you mark this as SOLVED please using [COLOR="Red"]Thread Tools[/COLOR] at the top of the page.

Thank you.

---

