---
title: "DHCP3 Configuration, WAN Problem"
date: 2011-09-07
forum: Networking &amp; Wireless
---

### Post by sdegan on 2011-09-07
Hi. I installed Ubuntu Server v11.04. My box is setup with two wireless cards, one connected to WAN, one connected to my LAN. I want it to act as a router. 

Today I tried sudo apt-get install dhcp3-server. That worked fine except the default dhcpd.conf file was not in the correct location that it should be. I later found that the system has itc-dhcp-server installed, so I removed dhcp3-server. Does anyone have any comment on that? Is one better than the other? Does it make sense that installing dhcp3-server would not download default config files if the ITC version is installed?

In addition, I can now no longer connect to the internet. eth(1) is connected to the WAN, while eth(0) is connected to my home network. I specified an IPv4 address for eth(0), and now I can no longer connect to the internet. Upon disabling eth(0) I still cannot connect. When I go into the Network Configuration in gnome, eth(0) shows up but eth(1) does not. Oddly enough, ifconfig shows an IP for eth(1), the WAN adapter, and the one I specified for eth(0). 

How can I get my internet connection back? And also, why doesn't eth(1) show up in the GUI Network Configuration window? It shows up in the Network Tools window, but not the former. WTF?

I appreciate any help I can get!!!

---

### Post by Iowan on 2011-09-07
I'd be a little curious to see the results of **route -n**. More than one default gateway will be a problem. Also, I presume the interfaces are in separate subnets...

---

### Post by sdegan on 2011-09-10
Hey Iowan. Thanks for the suggestion. I figured it out. I had the wrong interfaces listed in the configuration file, which caused a host of problems haha.

---

