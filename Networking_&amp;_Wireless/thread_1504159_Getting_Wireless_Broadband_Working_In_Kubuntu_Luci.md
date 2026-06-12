---
title: "Getting Wireless Broadband Working In Kubuntu Lucid"
date: 2010-06-07
forum: Networking &amp; Wireless
---

### Post by ..::| Dave89 |::.. on 2010-06-07
I've just completed switching both my laptop and desktop from Ubuntu 10.04 to Kubuntu 10.04, all seems to be working well, except that I can't get my Virgin Mobile HUAWEI E160E wireless broadband modem working.  I used to have it working flawlessly in Ubuntu, I've used the smae step as described in this post: [http://ubuntuforums.org/showthread.php?t=1014221](http://ubuntuforums.org/showthread.php?t=1014221) that worked for me with Ubuntu, but the Wireless Broadband tab is greyed out under the manage connections dialog.  Any help on this appreciated.  I'm running the 64-bit version of Kubuntu BTW.

Thanks in advance

---

### Post by omegadestroy on 2010-09-24
Hi

I'm completely new to the Linux world and badly needs help. I installed Kubuntu 10.04 two days ago and it has been a disaster because it has inconsistencies detecting the e1550. There are instances that it's working but after a reboot/hibernate it goes to a haywire. I need to delete and re-setup the mobile broadband connection settings once Kubuntu detects it after multiple reboots. Another thing I noticed is it's not being recognized as a USB modem to automatically connect as configured hence just a storage device when it's acting up. I'm also using Ubuntu 10.04 on the same netbook but I never got a problem using the same broadband connection. Is there a fix for this?

---

### Post by a_flj_ on 2011-01-22
K network manager won't show any tabs as active unless the plugins for the corresponding tabs are installed. You need to install network-manager-openvpn to get the VPN tab active, for instance.

I'm not sure what the network manager plugin for network manager is, but I recall you must install modemmanager and some more packages (I seem to recall usb-modeswitch was also required). Also, you have to check your driver.

I had a similar problem with a Huawei stick, I can't remember the build,and for some reason had to boot with the stick connected in order to get it going, there was no way around it. Still, installing the packages related to USB modem stuff was a must.

You also must make sure you have an up to date kernel and libraries and such, by running apt-get update/apt-get upgrade.

---

