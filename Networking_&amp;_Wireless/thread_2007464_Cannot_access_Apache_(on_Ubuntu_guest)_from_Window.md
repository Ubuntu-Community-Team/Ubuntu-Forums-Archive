---
title: "Cannot access Apache (on Ubuntu guest) from Windows host"
date: 2012-06-20
forum: Networking &amp; Wireless
---

### Post by confounder on 2012-06-20
Hi All,

I am new to the world of Linux and Ubuntu. I have Ubuntu (12.04 LTS) on an Oracle Virtualbox and the guest OS is Windows 7.

Apache2 is installed and running on Ubuntu. I can access the default page and phpmyadmin in Firefox on the guest. However, I cannot access the default site or phpmyadmin from any browser on Windows 7 (host). The site looks like it's trying to connect but get the 'cannot connect to website' error.

However, I can ping the guest from Windows 7.

Summary

Host: Windows 7 64 Bit
Guest: Ubuntu 12.04
Web Server: Apache 2
Firewall on Ubuntu: GUFW
IP address of guest: 192.168.0.2

Windows 7 host file contains 192.168.0.2 mywebserver.com

Any help would be appreciated.

Thanks.

---

### Post by confounder on 2012-06-20
Hi All,

I am an idiot. I also jumped the gun.

The issue was with the firewall. I needed to allow connections to the Ubuntu on the web server port (80).

The following article helped:

[http://www.techotopia.com/index.php/Using_gufw_and_ufw_to_Configure_an_Ubuntu_11.04_Firewall](http://www.techotopia.com/index.php/Using_gufw_and_ufw_to_Configure_an_Ubuntu_11.04_Firewall)

---

### Post by clayt0njknight on 2012-06-20
Glad you were able to find resolution so quickly!  Welcome to Ubuntu, and welcome to Ubuntu Forums! :)

---

