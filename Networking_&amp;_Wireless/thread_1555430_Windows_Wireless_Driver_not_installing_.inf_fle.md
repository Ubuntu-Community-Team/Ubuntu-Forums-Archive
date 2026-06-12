---
title: "Windows Wireless Driver not installing .inf fle"
date: 2010-08-18
forum: Networking &amp; Wireless
---

### Post by rathodsachin20 on 2010-08-18
Hi,
I have Dell Wireless N-card 1520 on my Dell Studio 15 laptop. I have installed Ubuntu10.04
in it.
My network card was not able to detect wireless connections. I have even installed 'Windows Wireless Driver' using ndiswrapper. I have latest driver for card. But when i click install .inf file , nothing happens or gets installed. Please someone give the solution.

---

### Post by JBAlaska on 2010-08-18
You can remove ndiswrapper and use the **Broadcom STA proprietary wireless driver** under **System, Administration, Hardware Drivers**.

---

### Post by rathodsachin20 on 2010-08-18
I have tried Brodcom driver as u suggested, it was not pre-installed. So, i installed it but it is having problems during installation and is not showing up in Hardware Drivers list.

Meanwhile, i again tried with ndiswrapper. This time, Wireless card driver got installed.
It is sayin 'Hardware present : Yes' .  But network is still not working. It is saying network UNCLAIMED.

---

### Post by JBAlaska on 2010-08-18
The Broadcom driver not showing up is a fairly common problem that I thought got fixed in lucid..guess not.

To fix this without having a net connection, put the Ubuntu LiveCD in your drive and go to: System, Administration, Software sources and check the box below "Installable from CDROM". Then open a terminal and do:

```
sudo apt-get update
```

Then:

```
sudo apt-get install bcmwl-kernel-source
```

Now reboot and select the STA driver. in System, Administration, Hardware Drivers.

---

### Post by rathodsachin20 on 2010-08-19
I have installed Ubuntu inside Windows 7 using .iso file. So i don't have CDROM. I tried using disc mounter in ubuntu. But it didnt work. I got following reply as given in attachment.

I downloaded driver from :   [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

The driver showed up in the list , but i got error message:
Failed to fetch cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release amd64 (20100429)]/pool/main/f/fakeroot/fakeroot_1.14.4-1ubuntu1_amd64.deb File not found


EDIT:

I have installed required packages manually.  The the driver got activated after reboot, but wireless connection is not yet detected.  Please help me.

---

### Post by rathodsachin20 on 2010-08-20
Finally, it got fixed. I installed manually 'bcmwl-kernel-source' from pool/restricted/b/bcmwl  directory in installation .iso file. Then activated wireless driver & it worked! 

Thanks for your help !

---

