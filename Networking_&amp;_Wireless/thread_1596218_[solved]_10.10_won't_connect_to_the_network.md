---
title: "[solved] 10.10 won't connect to the network"
date: 2010-10-14
forum: Networking &amp; Wireless
---

### Post by mordoc on 2010-10-14
All,

My issue was similar to many out there, I couldn't connect to my home network either over ethernet or wifi.  After an hour of search, I noticed that I could statically set the ip and all interaces would work.

So it's DHCP is it!  Have a look in your dhclient.conf file (/etc/dhcp3/dhclient.conf) and see if you have a line such as this near the top:

[INDENT]send host-name "<hostname>";[/INDENT]

I changed it to read:

[INDENT]send host-name "my-machine"; (or whatever your hostname is)[/INDENT]

Restarted the network stack with sudo /etc/init.d/networking restart and it was all good.

Hope this helps someone else!

---

