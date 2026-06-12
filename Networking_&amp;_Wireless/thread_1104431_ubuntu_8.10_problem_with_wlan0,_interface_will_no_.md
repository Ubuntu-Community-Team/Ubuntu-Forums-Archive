---
title: "ubuntu 8.10 problem with wlan0, interface will no longer configure"
date: 2009-03-23
forum: Networking &amp; Wireless
---

### Post by danebramaged on 2009-03-23
Hello to all:

When I installed Ubuntu, it worked just fine. Everything installed just fine so, I never became the master of manually configuring my wireless internet connection.

Now however, I've gone an installed (then uninstalled) wide-dchpv6-client (because it didn't finish the install according to synaptic package manager) and Ubuntu will not config the interface for wlan0 on the way up anymore and xfld (xnetcardconfig) is not successfull in automatically configuring my conection.

A live cd connects just fine.  I also uninstalled/re-installed the wireless linksys card (wlan0) but that made no difference. Everything else on the network is working just fine. 

ifconfig wlan0 up, actually works.
dhclient -r wlan0, returns with-> wmaster0: unknown hardware address 801

Obviously, I shouldn't have to reinstall my os just to configure a wireless nic so, any advice on the subject would be greatly appreciated.

---

