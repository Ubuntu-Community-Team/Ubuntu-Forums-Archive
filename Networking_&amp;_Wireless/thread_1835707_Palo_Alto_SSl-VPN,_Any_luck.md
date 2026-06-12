---
title: "Palo Alto SSl-VPN, Any luck?"
date: 2011-08-29
forum: Networking &amp; Wireless
---

### Post by Timster4life on 2011-08-29
First off, I apologize if I placed this in the wrong Forum, please let me know if I have and I will remove it ASAP!

Hello everyone, and thank you in advance for any help I may get!

My company has switched to a Palo Alto SSL-VPN connection VS there old windows integrated VPN.

I know Palo Alto has no direct Linux support...I was wondering if anyone by any means has had luck connecting to said VPN either a 3rd party program.. or maybe with something along the lines of Wine.

The client is Java based and supports both Windows and Mac OSX.

Any information that could be provided would be awesome!
:D

---

### Post by lkjoel on 2011-08-30
If the client is Java based, then it should work on Ubuntu too.

---

### Post by praseodym on 2011-08-30
You may want to install the closed-source java-version from Oracle instead of the open-source one:

```
sudo apt-get install --reinstall sun-java6-jre sun-java6-plugin
sudo update-alternatives --config java
sudo update-alternatives --config mozilla-javaplugin.so 
```
Choose the sun/oracle versions, respectively. Both java-runtimes can be installed in parallel.

---

### Post by Timster4life on 2011-08-31
Unfortunately, That did not work.. I am trying Wine & IE8 combo now see if that will..

When I navigate to the IP to down load the SSL-VPN software it says "We are sorry but we only support Windows and OSX at this time" (shortened version) Really frustrating! I love my netbook so much that it's practically all I use

Thanks to everyone who has replied thus far!!

---

### Post by lkjoel on 2011-08-31
Get Wine 1.3

---

### Post by atimonin on 2012-06-26
shrewsoft vpn client works with palo alto global protect.
The only thing you should do by hands:

sysconfig net.ipv4.conf.eth0.rp_filter=0

(or whatever net interface you use)
or permamnetly set it in /etc/sysconfig.d/...

---

### Post by Elfy on 2012-06-26
Closed.

---

