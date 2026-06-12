---
title: "Ubuntu 8.10, BCM4306, DHCP issues"
date: 2009-04-21
forum: Networking &amp; Wireless
---

### Post by sgtcasey on 2009-04-21
I just installed 8.10 on an old HP zv5430us laptop with a BCM4306 802.11b/g Wireless LAN Controller (rev 03) and had problems getting wlan0 to DHCP an IP address from my Buffalo WHR-G125 router running DD-WRT v24-sp1 firmware.  I am using the b43 drivers on my laptop which I installed after I was prompted.

Here is what I was seeing in the syslog file:

```

daveslaptop dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
daveslaptop dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
daveslaptop dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
daveslaptop dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
daveslaptop dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
daveslaptop NetworkManager: <info> Device 'wlan0' DHCP transaction took too long (>45s), stopping it.
daveslaptop NetworkManager: <info> wlan0: canceled DHCP transaction, dhcp client pid 6424

```

I decided to try tweaking some settings on the router and found if I disabled DHCP-Authoritative I was able to grab an IP and finally get onto my home network and out to the Internet.

You can find the DHCP-Authoritative option by connecting to your router and then going to Setup > Basic Setup then going to the Network Setup section and looking under Network Address Server Settings (DHCP).  Uncheck the box and try to reconnect via wireless.

I didn't see anything posted by anyone after a number of Google and Ubuntuforums.org searches so I figured I'd make a post for whoever might also run into this issue and find the workaround I am using useful.

Dave

---

