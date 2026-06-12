---
title: "VPN Client Not Connecting"
date: 2009-04-03
forum: Networking &amp; Wireless
---

### Post by Max Avion on 2009-04-03
Hello, 

I have installed network-manager-pptp to access my VPN connection which is run using a Microsoft PPTP server. After installing the application the VPN section in the network manager was no longer grayed out and I was able to enter my host/login credentials. First, it will not connect and I think that all the information is correct, ans second, right after asking for my keyring password the WLAN connection drops out and the network mgr icon in the panel disappears, the only way I can get this back is by logging on and off again. 

I am not that experienced with Linux Ubuntu but have used it for a little while and like it but need to be able to VPN and RDC to my work Windows PC. 

If anyone has some guidance or troubleshooting advice that they would be able to share it would be very much appreciated. Thank you in advance!

Regards,

Max

---

### Post by simplic8 on 2009-04-06
Hi Max,

I'm not sure about why your wireless network drops out, however you should be able to get around this for the time being until you work that one out by restarting the network component of ubuntu 

/etc/init.d/networking restart

As for the PPTP connection, please check my post in regards to setup instructions, skip the pptp package installation as it looks like you have already completed this.

[http://blog.simplic8.com/?p=7]("http://blog.simplic8.com/?p=7")

---

