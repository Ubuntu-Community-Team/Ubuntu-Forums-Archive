---
title: "Router &amp; DHCP server (for multiple subnets) on the same box"
date: 2009-06-15
forum: Networking &amp; Wireless
---

### Post by wowiesy on 2009-06-15
I plan to setup a DHCP server and a router(SERVER)  on the same box. The machine would have 3 NICs:
eth0 - 192.168.1.254
eth1 - 192.168.2.254
wlan0 - 192.168.3.254  (if I get the master mode working on this one)

The plan is to make this box the DHCP server for all of the 3 subnets.  There is a Linksys router which is the gateway to the internet (192.168.1.1) that can serve as the DHCP server for the 1.0/24 network, but the SERVER should still dynamically provide IP addresses to the 2.0/24 and 3.0/24 network.. 

Can this be done? The ideal way is to have each subnet have it's own DHCP server within its subnet. I read about ip helper addresses but I don't understand actually how it works for linux.

---

### Post by MaindotC on 2009-06-16
ip-helper address is a configuration in a router that tells the router where to forward DHCP requests.  If you have a DHCP server on a LAN, then any device that connects via a switch will easily have it's DHCP request answered by the DHCP server.  If a device connects to a LAN that does not have a DHCP server, then when the switch or router receives the DHCP requests, it needs to know where to send those requests, and that's where the helper address comes in.  If that's not configured properly, nothing that connects will be issued an address.  So anyway, I don't think that's really what you're looking for.

You probably can do as you stated as I believe anything is possible with an open-source distribution but I think you'll find it easier to do this one of two ways.  You can use just one adapter and configure /etc/dhcpd.conf to issue the addresses you wish for each subnet.

Another option is to use virtual machines and bind them to the adapters you wish and configure /etc/dhcpd.conf in each VM to suit your needs.  I did this with the help of a user [on virtualbox forums](http://forums.virtualbox.org/viewtopic.php?f=7&t=9165).  It seems ludicrous to set up a VM for dhcpd - a program that uses maybe 500 KB of memory - but I think if you follow the directions on that forum post you'll reach a much goal much more definitely.

There may be other options such as loading openwrt on your access point and configuring the dhcp server that comes with it.

---

### Post by dmizer on 2009-06-16
Piece of cake.

Install dnsmasq:
```
sudo apt-get install dnsmasq
```
Make a copy of the default conf file:
```
sudo cp /etc/dnsmasq.conf /etc/dnsmasq.conf-backup
```
Edit /etc/dnsmasq.conf
```
gksudo gedit /etc/dnsmasq.conf
```
Remove everything in the file and replace it with these lines:
```
dhcp-range=192.168.2.100,192.168.2.200
dhcp-range=192.168.3.100,192.168.3.200
```
Then configure your eth1 and wlan0 for static IP 192.168.2.1 and 192.168.3.1 respectively.

Restart dnsmasq:
```
sudo /etc/init.d/dnsmasq restart
```

You should be good to go.

Note ->
You may have to ditch (iow uninstall) the GUI network-manager in order to accomplish the necessary network configurations. In that case, you may want to refer to this thread: [http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)

---

### Post by MaindotC on 2009-06-16
Bah - I always make things so complicated :(

---

### Post by wowiesy on 2009-06-20
> **dmizer said:**
> 
dhcp-range=192.168.3.100,192.168.3.200[/code]Then configure your eth1 and wlan0 for static IP 192.168.2.1 and 192.168.3.1 respectively.

Restart dnsmasq:
```
sudo /etc/init.d/dnsmasq restart
```You should be good to go.



Does the static IPs need to be X.1? or any address as long as it's on the same subnet... ?

---

### Post by jonobr on 2009-06-20
Hello


An Ip address is an ip address so long as they are in the same subnet they are good.

Open to correction but using .1 is convention to denote default routers and gateways,

the only addresses that are off limits are the broadcast address and the network address.
so in a 192.168.1.X network with a class C subnet
192.168.1.0 is not allowed as thats the network address and 192.168.1.255 is not allowed as its the broadcast...
everything in between can be assigned to anything.

if the 192.168 had a class B address then 192.168.0.0 would not be allowed, nor would 192.168.255.255

for the same reason.

In every subnet , two ip address are generally not usable.
the rest are fair game.

Things do get a bit trickier when you subnet 
(i.e. 255.255.255.248) but the same rules really apply to that,

Scared of networking yet???

In the words of the great yoda .........You will be!!!
:-)

Cheers

---

### Post by dmizer on 2009-06-20
You can use any address that's not a part of the dhcp-range you set in /etc/dnsmasq.conf

Convention is to use .&#65297; because it's easy to remember and that will come in handy if you want to route traffic through the dhcp server later.

---

