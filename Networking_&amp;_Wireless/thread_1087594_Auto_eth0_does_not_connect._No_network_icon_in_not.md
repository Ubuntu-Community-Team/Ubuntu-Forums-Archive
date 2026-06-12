---
title: "Auto eth0 does not connect. No network icon in notification area."
date: 2009-03-05
forum: Networking &amp; Wireless
---

### Post by amkr on 2009-03-05
n00b here, please help!
I need the Auto eth0 for my pppoe connection. But just after I configured everything, in the next boot, Auto eth0 does not connect. Moreover, there is NO network icon in the notification area. Please help urgent.

---

### Post by Brandon.Viking on 2009-03-05
Maybe a little more detail on the setup or the problem would be helpful. Is the eth interface supposed to be using DHCP? Has the NetworkManager Applet been removed from the panel?

post the output of 'ps aux |  grep -i network'
should be similar to the following if it is running

> ps aux | grep -i network
root      8003  0.0  0.2   6408  2276 ?        Ss   12:27   0:00 /usr/sbin/NetworkManager
root      8014  0.0  0.3   7696  3520 ?        S    12:27   0:00 /usr/sbin/nm-system-settings --config /etc/NetworkManager/nm-system-settings.conf

hope that helps.
Regards,
Brandon.

---

