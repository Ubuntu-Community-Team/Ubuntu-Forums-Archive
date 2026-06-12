---
title: "Static IP problem"
date: 2010-03-15
forum: Networking &amp; Wireless
---

### Post by thep8ntballfreak on 2010-03-15
i have followed multiple guides to make my home server use a static ip address. no matter what i do it always reverts back to its dhcp address after about 2 minutes.

how do i get the static ip address to stick, or be permanant.

any and all help will be greatly appreciated

---

### Post by chili555 on 2010-03-16
Remove Network Manager:```
sudo apt-get remove --purge network-manager*
```Set up */etc/network/interfaces correctly.* Here is an example:```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.112
netmask 255.255.255.0
gateway 192.168.1.1
```Pick an address outside the range of the DHCP server in the router. If your router assigns DHCP addresses from x.100 to x.109 then static addresses should be set from x.110 up.

Populate */etc/resolv.conf*. Here is a sample:```
nameserver 192.168.1.1
```Restart networking:```
sudo /etc/init.d/networking restart
```Verify:```
ifconfig
ping -c3 www.google.com
```Post back so the searchers will know your result. Thanks.

---

### Post by Iowan on 2010-03-16
Just to throw out an alternative (ain't choices wonderful?): Since it seems to be fond of DHCP address, you can (probably) configure your DHCP server (router?) to issue a static lease based on MAC address (pick one outside DHCP range). Then the machine gets the same address, but needn't be reconfigured.
Without going down the "REAL servers don't have GUI's" road, does yours? If not, NM may not be (probably isn't) an issue. If so... see previous post. ;)

---

### Post by thep8ntballfreak on 2010-03-16
> **chili555 said:**
> Remove Network Manager:```
sudo apt-get remove --purge network-manager*
```Set up */etc/network/interfaces correctly.* Here is an example:```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.112
netmask 255.255.255.0
gateway 192.168.1.1
```Pick an address outside the range of the DHCP server in the router. If your router assigns DHCP addresses from x.100 to x.109 then static addresses should be set from x.110 up.

Populate */etc/resolv.conf*. Here is a sample:```
nameserver 192.168.1.1
```Restart networking:```
sudo /etc/init.d/networking restart
```Verify:```
ifconfig
ping -c3 www.google.com
```Post back so the searchers will know your result. Thanks.

I did all that exactly as posted. (Copy and Pasted.) The server which has no GUI kept a static IP for about 3 minutes and then it changed itself back to the DHCP address it has had since i installed Ubuntu Server a few days ago.

---

### Post by chili555 on 2010-03-16
Please run:```
sudo killall dhclient
sudo rm -f /var/run/dhclient.pid
sudo /etc/init.d/networking restart
```Is the behavior improved?

---

### Post by thep8ntballfreak on 2010-03-17
same result, it kept the static IP for maybe 3 minutes then back to the IP i don't want it to have. i have dd-wrt on my router, maybe that is the problem. My ubuntu server will not keep the static IP i give it though.

---

### Post by lisati on 2010-03-17
> **Iowan said:**
> Just to throw out an alternative (ain't choices wonderful?): Since it seems to be fond of DHCP address, you can (probably) configure your DHCP server (router?) to issue a static lease based on MAC address (pick one outside DHCP range). Then the machine gets the same address, but needn't be reconfigured.
Without going down the "REAL servers don't have GUI's" road, does yours? If not, NM may not be (probably isn't) an issue. If so... see previous post. ;)

I second this suggestion - I set my server's static IP address at the router. Letting the router manage IP addresses allocated to the various machines on my network can often simplify the process of managing settings at the computer's end; I've found this approach to work well with both Windows and Ubuntu.

---

### Post by chili555 on 2010-03-17
> **thep8ntballfreak said:**
> same result, it kept the static IP for maybe 3 minutes then back to the IP i don't want it to have. i have dd-wrt on my router, maybe that is the problem. My ubuntu server will not keep the static IP i give it though.Is reboot an option? I know we are all jealous of our killer uptimes.

---

### Post by thep8ntballfreak on 2010-03-17
> **lisati said:**
> I second this suggestion - I set my server's static IP address at the router. Letting the router manage IP addresses allocated to the various machines on my network can often simplify the process of managing settings at the computer's end; I've found this approach to work well with both Windows and Ubuntu.

This is what i did and it seems to work. Thanks for the help guys!!!

---

### Post by Iowan on 2010-03-17
Glad it worked - now just one more little detail...
[[SOLVED]]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")

---

### Post by arinekhen on 2011-12-14
Just want to say thanks. 

Thanks.

=]

---

