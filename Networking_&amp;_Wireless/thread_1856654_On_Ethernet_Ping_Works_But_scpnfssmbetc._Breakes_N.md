---
title: "On Ethernet Ping Works But scp/nfs/smb/etc. Breakes Network Entierly"
date: 2011-10-08
forum: Networking &amp; Wireless
---

### Post by arclance on 2011-10-08
I have two network connections on my computers wlan0 (wireless) and eth0 (ethernet).
The internet is accessed through wlan0 and eth0 is used for sharing files between my computers over the ethernet network.
The networks are configured so that they work at the same time so the internet can be accessed on wlan0 while sharing files at the same time over eth0.
I am experiencing no problems with wlan0.
However only ping works for more than 5 seconds on eth0.
Any other type of network usage causes the total loss of all traffic between the computers over eth0.
The eth0 problems are seen using a router or switch to connect the computers.
The same connections work over the wlan0 network but are too slow for what I am doing (Photo  Editing).
The network connections on my computers are configured this way.

_**Computer 1**_: Hosts Shared Files
**wlan0**: configured in network manager
_Wireless_
SSID: networks ssid
Mode: Infrastructure
BSSID:
Device MAC address: wireless pci card mac address
Cloned MAC address:
MTU: automatic
_Wireless Security_
Security: None
_IPv4 Settings_
Method: Manual
Address: 192.168.1.2
Netmask: 255.255.255.0
Gateway: 192.168.1.1
DNS servers: dns server ips
Search domains:
Require IPv4 addressing for this connection to complete: checked
           _Routes_
           Address: 192.168.1.2
           Netmask: 255.255.255.0
           Gateway: 192.168.1.1
           Metric: 1
           Use this network only for resources on its network: unchecked
_IPv6 Settings_
Method: Ignore

**eth0**: configured in network manager
_Wired_
Device MAC address: ethernet mac address
Cloned MAC address:
MTU: automatic
_802.1x Security_
Nothing
_IPv4 Settings_
Method: Manual
Address: 192.168.10.2
Netmask: 255.255.255.0
Gateway: 192.168.10.1
DNS servers: 192.168.10.1
Search domains:
Require IPv4 addressing for this connection to complete: checked
           _Routes_
           Address: 192.168.10.2
           Netmask: 255.255.255.0
           Gateway: 192.168.10.1
           Metric: 10
           Use this network only for resources on its network: checked
_IPv6 Settings_
Method: Ignore

_**Computer 2**_: Client For Shared Files
**wlan0**: configured in network manager
_Wireless_
SSID: networks ssid
Mode: Infrastructure
BSSID:
Device MAC address: 
Cloned MAC address:
MTU: automatic
_Wireless Security_
Security: None
_IPv4 Settings_
Method: Manual
Address: 192.168.1.3
Netmask: 255.255.255.0
Gateway: 192.168.1.1
DNS servers: dns server ips
Search domains:
Require IPv4 addressing for this connection to complete: checked
           _Routes_
           Address: 192.168.1.3
           Netmask: 255.255.255.0
           Gateway: 192.168.1.1
           Metric: 1
           Use this network only for resources on its network: unchecked
_IPv6 Settings_
Method: Ignore

**eth0**: configured in network manager
_Wired_
 Device MAC address: ethernet mac address
 Cloned MAC address:
 MTU: automatic
_802.1x Security_
 Nothing
 _IPv4 Settings_
 Method: Manual
 Address: 192.168.10.3
 Netmask: 255.255.255.0
 Gateway: 192.168.10.1
 DNS servers: 192.168.10.1
 Search domains:
 Require IPv4 addressing for this connection to complete: checked
            _Routes_
            Address: 192.168.10.3
            Netmask: 255.255.255.0
            Gateway: 192.168.10.1
            Metric: 10
            Use this network only for resources on its network: checked
 _IPv6 Settings_
 Method: Ignore

Google searches and forum posts have gotten me to this point but I have no idea what is wrong now.
I would prefer to use the switch I have to connect the computers because it is 1000 Mbit and the router is not.
Could anyone please help me figure out how to get this working correctly?

---

### Post by arclance on 2011-10-20
Anyone have any idea about how to make this work?

---

### Post by arclance on 2011-11-06
After trying a ten year old 10/100 pci ethernet card in computer2 and seeing that it was using the same driver as the brand new gigabit port on the motherboard I did a more specific search and confirmed that Ubuntu had installed the wrong driver for my motherboard ethernet port.
After removing the incorrect driver and building and installing the correct driver everything works!
[I found the solution here.]("http://penkovvladimir.blogspot.com/2011/08/ubuntu-network-with-p8p67-motherboard.html")

---

