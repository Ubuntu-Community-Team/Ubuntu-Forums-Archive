---
title: "Another Lucid Wifi Issue (this one's different!)"
date: 2010-07-31
forum: Networking &amp; Wireless
---

### Post by zoso375 on 2010-07-31
Yes, I have yet another case of wireless issues in Lucid.  This one popped up a couple of weeks after a fresh install, after which I have had no problems with wireless, until this one.  And it's odd: I can connect to the router very quickly, and everything appears as normal.  I'm connected, link quality's good, etc.  But nothing can connect to the web.  The weird part is, it doesn't even appear to try. When I open Chrome, there's no attempt to connect- it instantly says "unable to display web page."  Ditto for Pidgin- no delay on startup as it tries to connect, just an instant failure. It's as if something's telling the system that there's no connection, when in fact there is.  

Here's the output of ```
sudo lshw -C network
```:

*-network
     description: Wireless interface
     physical id: 1
     bus info: usb@1:7
     logical name: wlan0
     serial: 00:18:4d:13:f1:47
     capabilities: eternet physical wireless
     configuration: broadcast=yes driver=rt18187 driverversion=2.6.32-24-generic firmware=N/A ip=10.42.43.1 link=yes multicast=yes wireless=IEEE 802.11bg

and the output of ```
iwconfig
```

IEEE 802.11bg ESSID:"N8ASJ"
Mode:Managed Frequency:2.412 GHz Access Point: 00:24:D2:46:87:46
Bit Rate=54 Mb/s Tx-Power=20Dbm
Retry long limit:7 RTS thr:off Fragment thr:off
Power Management:off
Link Quality=58/70 Signal level=-52 dBm
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

Note that I used ```
sudo iwconfig wlan0 rate 54M
``` to change the bit rate, which was previously showing 1Mb/s

To sum up, I'm lost.

---

### Post by marvselby on 2010-07-31
It would appear you are connected to the router.  Try "ifconfig wlan0" and see if it shows an address assigned to your machine. (e.g. 192.168.1.100)  If it doesn't then try "sudo dhclient wlan0" which will use DHCP to assign your machine an IP address.

Another approach is to shut down your network connection using "sudo ifconfig wlan0 down" then "sudo ifconfig wlan0 up" to bring it back up, and finally "sudo dhclient wlan0" to get an IP address using DHCP

As it stands now, can you ping the router?  (e.g. "ping 192.168.1.1")  If you can, then try pinging an Internet address like "ping 4.2.2.2"  If the pings work then you do have an IP address.  The problem then is one of DNS and probably is because you don't have a DNS server either set up in your router or possibly you don't have the router's IP address set as your gateway.

Hope this helps.  BTW, are there any other machines connected to your router and do they work?

---

### Post by zoso375 on 2010-07-31
Well, as it turns out, this is human error. Apparently my roommate tried to share the connection to troubleshoot his laptop.  As soon as I unshared on ipv4 settings, all was well.  Sorry to bother :)

---

