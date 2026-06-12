---
title: "connect from command line"
date: 2011-05-08
forum: Networking &amp; Wireless
---

### Post by l3ecl on 2011-05-08
I can connect from my internet using GUI just fine, but when I try to use the command line, I get stuck.

This is a sample session:


[```
jk@Ubuntu /]$ sudo ifconfig wlan0 down
[jk@Ubuntu /]$ sudo dhclient -r wlan0
[jk@Ubuntu /]$ sudo ifconfig wlan0 up
[jk@Ubuntu /]$ sudo iwconfig wlan0 essid "2WIRE868"
[jk@Ubuntu /]$ sudo iwconfig wlan0 key 555555555
[jk@Ubuntu /]$ sudo iwconfig wlan0 mode Managed
[jk@Ubuntu /]$ sudo dhclient wlan0

```

And then nothing happens. I'm not connected to the internet. 

I don't really know whats happening. I don't get any errors or warnings. When I did get the out of 'dmesg', I got "wlano0: link is not ready"

---

