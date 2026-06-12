---
title: "DGE-530T with Marvell Yukon 88E8001 chipset Driver patch"
date: 2010-01-23
forum: Networking &amp; Wireless
---

### Post by fetanyl on 2010-01-23
I was wondering if anybody can help me telling me where i could get a driver to patch my DGE-530T with a Marvell Yukon 88E8001 chipset so that i can use aircrack-ng

My OS is Ubuntu 9.10 and I am running it on an HP Pavilion dv7 1020us 

thank you for your help

---

### Post by mathia on 2010-09-20
> **fetanyl said:**
> I was wondering if anybody can help me telling me where i could get a driver to patch my DGE-530T with a Marvell Yukon 88E8001 chipset so that i can use aircrack-ng

My OS is Ubuntu 9.10 and I am running it on an HP Pavilion dv7 1020us 

thank you for your help

Hi,

**[B]Installing Marvell Yukon 88E8001 driver on 9.10**:[/B]

Please install the following driver as follows:
[http://www.marvell.com/support.html](http://www.marvell.com/support.html)  -> "88E8001 Search" -> Kernel 2.6.x Linux Driver Install Package for Yukon Devices	Linux 2.6 - Fedora v10.85.9.3

 $ sudo bash ./install.sh

and let me know if it works.

Have a lot of fun ...:razz:

---

### Post by mannam33 on 2011-08-25
Hi i have the common problem with the wireless under Linux. The version i use i s 10.04 LTS and the internet adaapter is Marvel Yukon 88e8001. Please anybody who can help me to do it because i am a newbie and please make it in simple steps 
THANKS

---

### Post by Nouiz on 2012-01-10
Hi,

there is multiple version of this card. The old card should have the driver directly in the kernel even for some older ubuntu version. But the newer card (revision C1 for me) is only supported in ubuntu 11.10. That was my problem. I fixed it by upgrading my computer to this version.

In the case you lost your motherboard network port and you have only this card, you can update ubuntu by putting the installer of 11.10 on a CD or usb stick. In the installer they will give you the choice to upgrade your installation. This can delete installed program that are not in the new version, but at least, you will have a working network port.

So as the driver is in the kernel, you don't need to compile any driver. With the kernel version that support the card version you have, all should be automatic from that point.

---

### Post by Vpc on 2012-03-24
> **Nouiz said:**
> Hi,

there is multiple version of this card. The old card should have the driver directly in the kernel even for some older ubuntu version. But the newer card (revision C1 for me) is only supported in ubuntu 11.10. That was my problem. I fixed it by upgrading my computer to this version.

In the case you lost your motherboard network port and you have only this card, you can update ubuntu by putting the installer of 11.10 on a CD or usb stick. In the installer they will give you the choice to upgrade your installation. This can delete installed program that are not in the new version, but at least, you will have a working network port.

So as the driver is in the kernel, you don't need to compile any driver. With the kernel version that support the card version you have, all should be automatic from that point.

I also found that upgradng to 11.10 from 10.04 enabled internet access for D-link's DGE-530T, revision C1. The Intel 82579V Gigabit Ethernet Controller (on the Intel DP67DE motherboard) also didn't work with 10.04 but worked with 11.10.

---

