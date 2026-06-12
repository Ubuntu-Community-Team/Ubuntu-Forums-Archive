---
title: "Static IP with WEP security"
date: 2011-03-10
forum: Networking &amp; Wireless
---

### Post by eddierb on 2011-03-10
I recently switched to WEP encryption from a functional WPA encryption and I've been having problems since (I need WEP for another device and I understand it's less secure.)

I tried updating /etc/network/interfaces for the new network using the information here: [http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch13_:_Linux_Wireless_Networking#WEP_Encryption_Configuration_2]("http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch13_:_Linux_Wireless_Networking#WEP_Encryption_Configuration_2")

interfaces is now: 
```
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet static
    address 192.168.1.50
    netmask 255.255.255.0
    wireless-key <correct key>
    wireless-essid <correct ESSID>
```

Is there anything wrong with the above?

There is a chance I've made matters worse in my frustration... What troubleshooting steps can I take?

---

### Post by chili555 on 2011-03-10
> Is there anything wrong with the above?Yep.```
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet static
    address 192.168.1.50
    netmask 255.255.255.0
    [COLOR="Red"]gateway 192.168.1.??[/COLOR]
    wireless-key <correct key>
    wireless-essid <correct ESSID>
```Be sure the assigned address is outside the range of the DHCP server in the router. Then do:```
sudo ifdown wlan0 && sudo ifup wlan0
ping -c3 192.168.1.??
```^^^The address of the router.

Be sure to fill in /etc/resolv.conf with appropriate DNS nameservers. Post back if we can help further.

---

### Post by eddierb on 2011-03-10
perfect - thanks chilli

---

### Post by eddierb on 2011-03-14
I thought this was fixed but I'm still having issues.

I'm able to get on the network but it seems to drop off after a short amount of time.  I'm forwarding a port for a game server and when I fall off the network the server stops being accessible.  The only way to fix this is to use the /etc/init.d/networking restart command.

When I use the above command I get a "RTNETLINK answers: No such process" warning though the connection is restored (for a short time).

The server was running very well previously on the same IP (outside my router's DNS range) with WPA encryption.

Oh and I wasn't sure what this meant: 
> Be sure to fill in /etc/resolv.conf with appropriate DNS nameservers. Post back if we can help further.
I don't have a file called resolv.conf, only a directory etc/resolvconf/

Any troubleshooting steps/fixes I should try?

Edit: This is my current interfaces file
```
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet static
   address 192.168.1.50
   netmask 255.255.255.0
   gateway 192.168.1.1
   wireless-key <key>
   wireless-essid <essid>
```

---

### Post by chili555 on 2011-03-14
> I don't have a file called resolv.conf, only a directory etc/resolvconf/Oh, but I bet you do:```
cat /etc/resolv.conf
```> it seems to drop off after a short amount of time. It is more likely a driver problem. Please post:```
sudo lshw -C network
```We'll see what we can do.

---

### Post by eddierb on 2011-03-15
You were right:
```
me@here:~$ cat /etc/resolv.conf
nameserver 192.168.1.1
```

And
```
me@here:~$ sudo lshw -C network
  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: wlan0
       version: 02
       serial: 00:1b:77:c8:14:fd
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 ip=192.168.1.50 latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:29 memory:f9fff000-f9ffffff
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:1c:23:96:93:0a
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half ip=192.168.1.50 latency=64 link=no multicast=yes port=twisted pair speed=10MB/s
       resources: irq:17 memory:f9bfe000-f9bfffff
```

Anything interesting there?

---

### Post by chili555 on 2011-03-15
You *do* have a file /etc/resolv.conf and it looks correct.

The driver iwl3945 is usually pretty reliable. I wonder what kind of signal strength you have:```
iwconfig wlan0 | grep Link
```Anything below 40/70 is quite tricky to stay connected to, in my experience.

Perhaps you have radio frequency interference on the router's frequency. Most are set by default on channel 6. I have better luck on channel 11.

Does your router have a signal strength setting? Is it at maximum? Please see attached. Finally, you might try:```
sudo ifdown wlan0
sudo rmmod -f iwl3945
sudo modprobe iwl3945 swcrypto=0
sudo ifup wlan0
```If that helps, we'll need to write one short file to make it persistent.

---

### Post by eddierb on 2011-03-15
Hmm could it be that I just had poor signal strength and am just assuming the worst because the problems started when I switched encryption?  The strength in my room varies from 51 at best to 35 in the laptop's original position.

The connection has been pretty stable this evening in a new position...

Thanks for your thorough help Chilli, hopefully I won't need to reopen this thread again.

Just wondering if there were any settings/scripts that would allow the server to recover after a network disconnect?  /etc/init.d/networking restart manually works for the time being.

---

