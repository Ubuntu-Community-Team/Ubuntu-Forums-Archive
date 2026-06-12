---
title: "how to connect to a wireless repeater manually?"
date: 2011-03-27
forum: Networking &amp; Wireless
---

### Post by jujubees on 2011-03-27
network manager would re-establish my connection every few minutes causing lag while gaming, so i uninstalled it.
i can manually connect to my wireless router using this script:

#!/bin/bash
sudo ifconfig wlan0 down
sudo iwconfig wlan0 essid "dd-wrt"
sudo iwconfig wlan0 ap 00:23:69:5C:A9:71
sudo ifconfig wlan0 192.168.1.131
sudo route add default gw 192.168.1.1
sudo ifconfig wlan0 up
exit 0

my question is: What do i change in my script so I can connect to the repeater I just set up?

---

### Post by jujubees on 2011-03-31
any1?

---

### Post by Fboy on 2012-02-09
hey,

i'm having the same problem as you. i notice the thread is old, i'm hoping you got your solution in the end? maybe you could point me in the right direction.

cheers!

---

