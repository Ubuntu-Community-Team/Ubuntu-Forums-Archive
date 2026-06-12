---
title: "Is It Ubuntu or Firefox?"
date: 2008-12-24
forum: Networking &amp; Wireless
---

### Post by gregorygarza@hotmail.com on 2008-12-24
I just install Ubuntu 8.10.  I show that I am able to connect to both wired and wireless networks; I can even pull up ip addresses, subnet mask, gateway, and DNS for both.  I've disabled the wireless and plugged in, but when I open Firefox I get an "Address Not Found" page when I try to open ANY Web site.  I've unplugged and activate wireless and still get the same erro page.  I've concluded that the problem lies with Firefox since I'm able to join networks.  What do I have to do to Firefox to get on the Internet? Is is Firefox or is it privileges?  Please email me at [email]gregorygarza@hotmail.com[/email] if you can help me out.

---

### Post by dmizer on 2008-12-24
You'll find that very few people will be willing to email you directly. But most of us are more than willing to post support here.

You should try disabling ipv6 according to this howto: [https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4](https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4)

---

### Post by gregorygarza@hotmail.com on 2009-01-01
Ok, I went to the links you gave, entered the first command (sudo sh -c 'echo blacklist ipv6 >> /etc/modprobe.d/blacklist.local').  rebooted, and typed (ip a | grep inet6) to show whether or not ipv6 disabled.  It did.  Still, I can connect to the Internet.  I am pulling an ip address, broadcast, subnet, default route, primary and seconday DNS.  Please help.

---

### Post by dmizer on 2009-01-04
Sorry to hear that it did not help.

Now try using different DNS servers according to this howto: [https://www.opendns.com/homenetwork/start/device/ubuntu](https://www.opendns.com/homenetwork/start/device/ubuntu)

Note: be sure to follow the directions under "To avoid having your settings get revoked after reboots, or after periods of inactivity, do this:"

---

### Post by dmizer on 2009-01-04
Sorry to hear that it did not help.

Now try using different DNS servers according to this howto: [https://www.opendns.com/homenetwork/start/device/ubuntu](https://www.opendns.com/homenetwork/start/device/ubuntu)

Note: be sure to follow the directions under "To avoid having your settings get revoked after reboots, or after periods of inactivity, do this:"

---

