---
title: "Trying to connect to wireless network through the terminal"
date: 2011-03-19
forum: Networking &amp; Wireless
---

### Post by oldmankit on 2011-03-19
Hello,

Sometimes I use my laptop and don't have a mouse.  Any mouse.  The touchpad is broken.  In these instances it'd be great if I could connect to a wireless network entirely through the console.  I've done a bit of searching and found the following:
```

sudo iwlist scan 
sudo ifconfig wlan0 up
sudo iwconfig wlan0 essid <YOUR WIRELESS ROUTER's ESSID>
sudo iwconfig wlan0 key <YOUR KEY>
sudo dhclient wlan0 

```The first four commands don't display anything in the terminal.  On the final one:
```

Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/wlan0/00:19:d2:81:eb:0d
Sending on   LPF/wlan0/00:19:d2:81:eb:0d
Sending on   Socket/fallback
DHCPREQUEST of 192.168.1.10 on wlan0 to 255.255.255.255 port 67
DHCPREQUEST of 192.168.1.10 on wlan0 to 255.255.255.255 port 67
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 19
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
No DHCPOFFERS received.
Trying recorded lease 192.168.1.10
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.

--- 192.168.1.1 ping statistics ---
1 packets transmitted, 0 received, +1 errors, 100% packet loss, time 0ms



No working leases in persistent database - sleeping.

```Well, when I'm usin the gui (nm-applet) it works fine. Using the same network and password.  What am I doing wrong?

---

### Post by oldmankit on 2011-03-24
bump

---

### Post by moehabibi on 2011-03-24
double bumb

---

### Post by l3ecl on 2011-05-08
i'm having the same issues, has anyone figured it out yet?

---

### Post by cipherboy_loc on 2011-05-08
This didn't work on Ubuntu last time I tried it, but it works on Gentoo.

Try installing WICD (WARNING! REPLACES NETWORK-MANAGER; KEEP THE NETWORK MANAGER PACKAGES HANDY IF IT DOESN'T WORK) and use the wicd-curses program to connect. Not tested on Ubuntu, but works fairly well on Gentoo. Don't say I didn't warn you.


Cipherboy

---

