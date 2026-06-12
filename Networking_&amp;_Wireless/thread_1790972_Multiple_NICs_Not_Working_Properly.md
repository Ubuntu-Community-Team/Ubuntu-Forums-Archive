---
title: "Multiple NICs Not Working Properly"
date: 2011-06-25
forum: Networking &amp; Wireless
---

### Post by MrSchism on 2011-06-25
My setup:

I've looked around for an answer to this and haven't found one that really did too much to help.

I set up the isc-dhcp-server software on my kubuntu 11.04 box and was  receiving an issue saying that no connection was bound to eth3 (my PCI  NIC).  Eth0 is onboard.  Eth1 and Eth2 are physically removed from the  system.

I edited my /etc/network/interfaces file.  It initially only the following entry:
```
auto lo
iface lo inet loopback
```

Oddly enough, my eth0 was working fine.  I added the following:
```
auto eth3
iface eth3 inet static
address 192.168.1.4
subnet 255.255.255.0
```Now here's where the issue really shows up:

Eth0 won't accept connections.  It shows up on my router setup page but  doesn't have a correct name in my "attached devices" area and isn't  getting the IP it should be getting.

Eth3 accepts local connections (SSH and the like) but when I try to  connect to the internet, I get nothing when eth3 is the connection used  to get to the router.

When I add the following line to my /etc/network/interfaces file
```
auto eth0
iface eth0 inet dhcp
```the following appears in my ifconfig
```
eth0:avahi Link encap:Ethernet  HWaddr 00:30:67:6c:e5:6a  
          inet addr:169.254.8.233  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:41 Base address:0x6000 

```The overall goal is that I need to get eth0 to get internet and eth3 to  serve dhcp connections so I can image machines/network boot off of eth3  and still have internet access through eth0.

What would I have to change to make it work?

---

### Post by MrSchism on 2011-06-25
If you need any additional information, please let me know.

---

### Post by MrSchism on 2011-06-26
Okay... any suggestions as to where I'd look for the solution to this?

I'm getting kinda desperate to solve this. I've been working on the DHCP server/NIC setup issues for two weeks.... and I've been working on the overall project for over 3 months.

Please.  Any help would be appreciated.

---

### Post by MrSchism on 2011-06-27
I found an article over at cyberciti that explains some of it.  The article is located at [http://www.cyberciti.biz/faq/setting-up-an-network-interfaces-file/](http://www.cyberciti.biz/faq/setting-up-an-network-interfaces-file/)

It says to try the following: 
```
# Two ethernet interfaces, one connected to a trusted LAN, the other to 
# the untrusted Internet. If their MAC addresses get swapped (because an 
# updated kernel uses a different order when probing for network cards, 
# say), then they don't get brought up at all.   

auto eth0 eth1
  iface eth0 inet static
      address 192.168.42.1
      netmask 255.255.255.0
      pre-up /path/to/check-mac-address.sh eth0 11:22:33:44:55:66
      pre-up /usr/local/sbin/enable-masq
  iface eth1 inet dhcp
      pre-up /path/to/check-mac-address.sh eth1 AA:BB:CC:DD:EE:FF
      pre-up /usr/local/sbin/firewall
```
But I couldn't find a script that checks for mac addresses.  I opted for the following:
```
 auto eth0 eth1
  iface eth0 inet static
      address 192.168.1.4
      netmask 255.255.255.0
      network 192.168.0.0
  iface eth3 inet static
      address 192.168.1.4
      netmask 255.255.255.0
      network 192.168.0.0  
```

Now neither seems to work properly.

---

### Post by SeijiSensei on 2011-06-27
Go back to your original configuration and then edit /etc/default/dhcp3-server and put "eth3" in the INTERFACES line like this:

```
# On what interfaces should the DHCP server (dhcpd) serve DHCP requests?
#       Separate multiple interfaces with spaces, e.g. "eth0 eth1".
INTERFACES="eth3"

```

---

### Post by MrSchism on 2011-06-30
It's listed like that.  I have no problem serving the DHCP on eth3.  It just make it so that eth0 won't work at all.

---

### Post by SeijiSensei on 2011-07-01
What's the result of running "route -n"?

My guess is that the default gateway isn't being set properly.

---

