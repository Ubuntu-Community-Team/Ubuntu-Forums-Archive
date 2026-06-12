---
title: "Can't connect to ad-hoc network"
date: 2011-10-09
forum: Networking &amp; Wireless
---

### Post by xnevermore on 2011-10-09
I'm trying to share my internet connection from one ubuntu laptop to another, so I created a new wireless network through network manager in ad hoc mode, and made sure the ipv4 settings were set to "Shared to other computers". Then, on the other computer, I tried to connect to the adhoc network, but it keeps timing out.

Here's the relevant part of the syslog from the computer that's trying to connect:
```
dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
dhclient: DHCPDISOCVER on wlan0 to 255.255.255.255 port 67 interval 12
dhclient: DHCPDISOCVER on wlan0 to 255.255.255.255 port 67 interval 15
dhclient: DHCPDISOCVER on wlan0 to 255.255.255.255 port 67 interval 14
NetworkManager[2230]: <warn> (wlan0): DHCPv4 request timed out.
```

Meanwhile, on the host that created the network, it looks like this:
```

Oct  9 04:12:15 buk dnsmasq-dhcp[19791]: DHCPDISCOVER(eth1) 00:1a:73:1d:01:30 
Oct  9 04:12:15 buk dnsmasq-dhcp[19791]: DHCPOFFER(eth1) 10.42.43.22 00:1a:73:1d:01:30 
Oct  9 04:12:29 buk dnsmasq-dhcp[19791]: DHCPDISCOVER(eth1) 00:1a:73:1d:01:30 
Oct  9 04:12:29 buk dnsmasq-dhcp[19791]: DHCPOFFER(eth1) 10.42.43.22 00:1a:73:1d:01:30 
Oct  9 04:12:34 buk dnsmasq-dhcp[19791]: DHCPDISCOVER(eth1) 00:1a:73:1d:01:30 
Oct  9 04:12:34 buk dnsmasq-dhcp[19791]: DHCPOFFER(eth1) 10.42.43.22 00:1a:73:1d:01:30 
Oct  9 04:12:46 buk dnsmasq-dhcp[19791]: DHCPDISCOVER(eth1) 00:1a:73:1d:01:30 
Oct  9 04:12:46 buk dnsmasq-dhcp[19791]: DHCPOFFER(eth1) 10.42.43.22 00:1a:73:1d:01:30 
Oct  9 04:13:04 buk dnsmasq-dhcp[19791]: DHCPDISCOVER(eth1) 00:1a:73:1d:01:30 
Oct  9 04:13:04 buk dnsmasq-dhcp[19791]: DHCPOFFER(eth1) 10.42.43.22 00:1a:73:1d:01:30 
Oct  9 04:13:16 buk dnsmasq-dhcp[19791]: DHCPDISCOVER(eth1) 00:1a:73:1d:01:30 
Oct  9 04:13:16 buk dnsmasq-dhcp[19791]: DHCPOFFER(eth1) 10.42.43.22 00:1a:73:1d:01:30

```

So it seems like the host that created the network is getting the dhcp requests and is trying to send back offers, but the other host isn't receiving them for some reason.

Does anyone have any ideas?

---

