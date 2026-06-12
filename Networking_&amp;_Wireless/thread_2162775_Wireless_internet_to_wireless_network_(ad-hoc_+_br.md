---
title: "Wireless internet to wireless network (ad-hoc + bridge +hotspot)"
date: 2013-07-15
forum: Networking &amp; Wireless
---

### Post by sendmikemail on 2013-07-15
I am looking for a solution to my conundrum.

At my marina we are provided with a single web login for the wireless internet. This creates conflict in the family when multiple devices are used. 

Previously in windows, I have created a hosted network in 'netsh'. This enabled me to log into the marinas internet service under their ssid/passphrase and with the same wireless adapter(old laptop), broadcast my own ssid/passphrase and connect multiple devices that way(hotspot). It would generate a ip range different from the marina, and bridge through the two connections.

Worked great, but with a recent upgrade in my media pc I now run ubuntu 12.04 and this config has left me stumped.
 
Most of the 1000+ pages in the forum are concerned with wired to wireless ad-hocs(hotspots). This is not the solution I need.

A 'point' in the right direction would make my tired eyes very happy.

Tks....

---

### Post by prodigy_ on 2013-07-15
"Hosted Network" in Windows is Wi-Fi virtualization. You should be able to achieve the same in Linux with iw and hostapd (maybe even without hostapd if you actually use ad-hoc):
[http://wireless.kernel.org/en/users/Documentation/iw/vif](http://wireless.kernel.org/en/users/Documentation/iw/vif)
[https://wiki.archlinux.org/index.php/Software_Access_Point](https://wiki.archlinux.org/index.php/Software_Access_Point)
[http://nims11.wordpress.com/2012/04/27/hostapd-the-linux-way-to-create-virtual-wifi-access-point/](http://nims11.wordpress.com/2012/04/27/hostapd-the-linux-way-to-create-virtual-wifi-access-point/)
[http://nims11.wordpress.com/2013/05/22/using-hostapd-with-dnsmasq-to-create-virtual-wifi-access-point-in-linux/](http://nims11.wordpress.com/2013/05/22/using-hostapd-with-dnsmasq-to-create-virtual-wifi-access-point-in-linux/)

Then you'll need to enable routing and set up NAT:
[http://www.revsys.com/writings/quicktips/nat.html](http://www.revsys.com/writings/quicktips/nat.html)

---

### Post by sendmikemail on 2013-07-19
thx, lots to digest

---

