---
title: "ditched network manager to eliminate lag spikes"
date: 2011-03-25
forum: Networking &amp; Wireless
---

### Post by jujubees on 2011-03-25
A while back I removed the network manager in favor of manually configuring my wireless network(eliminate lag spikes).  I use this script to connect to my network:

#!/bin/bash
sudo ifconfig wlan0 down
sudo iwconfig wlan0 essid "dd-wrt"
sudo iwconfig wlan0 ap 00:23:69:5C:A9:71
sudo ifconfig wlan0 192.168.1.131
sudo route add default gw 192.168.1.1
sudo ifconfig wlan0 up
exit 0

Today I set up a wireless repeater and I am completely lost as to what to change/add to my script so I can connect to it.

---

### Post by jujubees on 2011-03-25
*tried to* change thread title

---

