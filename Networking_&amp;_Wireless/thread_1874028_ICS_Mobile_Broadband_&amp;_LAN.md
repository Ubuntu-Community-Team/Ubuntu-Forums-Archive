---
title: "ICS Mobile Broadband &amp; LAN"
date: 2011-11-02
forum: Networking &amp; Wireless
---

### Post by SilvaRizla on 2011-11-02
Hi there,

I need to configure internet connection sharing through mobile mobile broadband so that other machines on the LAN can share t.  My setup is as follows:

3G Mobile Net -- Old Desktop ----  BELKIN N Routher (No inet access) -- Other machines on the LAN

The old desktop has a wired connection to the router and and mobile broadband plugged in to a USB port.  I can connect to both the router and the 3G, however, if ethernet is connected to the desktop at the same time as the 3g card no nternet is available.  I am assuming that ubuntu then expects WAN to be available from the router, but there is no WAN due to my location.

Does anybody know how I'd go about sharing the mobile bb with the lan?

Many thanks

---

### Post by SilvaRizla on 2011-11-02
bump...

Still having no joy with this, I have tried sharing the eth0 connection through networkmanager and the 2 cards worked together briefly on different ip ranges however there was no way to share the mobile connection, then the router would kick the eth0 connection and not allow subsequent ones.

It seems to be an option to create a new wireless network with a spare wifi card and share it that way (which meets my needs fine) but my test card is not supported by default.  I have a spare rt8187l card that i will try tomorrow

---

### Post by jonobr on 2011-11-02
Did you follow the [HowTo]("https://help.ubuntu.com/community/Internet/ConnectionSharing") specifically the iptables piece?

---

### Post by SilvaRizla on 2011-11-02
Ah....

> Note: in the case of connecting a router, especially one with wireless, where you want the users to share your connection:

Check before you start (in Synaptic or with dpkg-query -l dnsmasq*) that dnsmasq-base is installed and that dnsmasq is not installed. Install or uninstall as appropriate (see next section).
After connecting the router, to enable masquerading, type: sudo iptables -t nat -A POSTROUTING -j MASQUERADE

I was not aware of this extra step, it may indeed be the key - i;ll take a look, thanks

---

### Post by jonobr on 2011-11-02
and the truth shall set you free :D

---

### Post by SilvaRizla on 2011-11-03
No joy at all today, dnsmasq-base was already installed.

There seems to be a bug in network manager concerning creating a new wifi network too so I'm wondering if its connected.  I'm going to try and config manually via iptables and see how far I get.  For those interested the wifi bug is listed here:

[https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/801313]("https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/801313")

---

### Post by SilvaRizla on 2011-11-10
It was a no go with ip-tables too so I do think its a bug in 11.10 - I ended up buying a TP-Link 3 router from amazon, £25 job done :cool:

---

