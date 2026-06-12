---
title: "nic teaming in 12.04"
date: 2012-05-01
forum: Networking &amp; Wireless
---

### Post by LCPSWolf on 2012-05-01
Perhaps this belongs in a different list - I'm suprised I found nothing similar here.  

Anyway :)  I'm attempting to do NIC teaming / bonding with server 12.04.

I've found a couple examples, but nothing that I've had any luck with:

[https://help.ubuntu.com/community/UbuntuBonding](https://help.ubuntu.com/community/UbuntuBonding)

[http://www.stgraber.org/2012/01/04/networking-in-ubuntu-12-04-lts/](http://www.stgraber.org/2012/01/04/networking-in-ubuntu-12-04-lts/)

I've got a base load of server 12.04 on an intel server, 2 NIC's.  I can set them individually just in with /etc/network/interfaces of:

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp
```Both interfaces get IP addresses like this.

I put in any of the bonding examples, and no interfaces come up.

Any thoughts?

Damian

---

### Post by Gyokuro on 2012-05-01
Hi

Looks good but you are missing the bonding part in your configuration - this guide should help you to achieve your goal ([https://help.ubuntu.com/community/UbuntuBonding](https://help.ubuntu.com/community/UbuntuBonding))

---

### Post by drdos2006 on 2012-05-01
Try these posts.

[http://ubuntuforums.org/showthread.php?p=11320085#post11320085](http://ubuntuforums.org/showthread.php?p=11320085#post11320085)

[http://ubuntuforums.org/showthread.php?t=1842656](http://ubuntuforums.org/showthread.php?t=1842656)

[http://ubuntuforums.org/showthread.php?t=1840543](http://ubuntuforums.org/showthread.php?t=1840543)

regards

---

### Post by MiLoX on 2012-10-12
Were you able to figure it out?? I think I am on the same side..

---

### Post by MiLoX on 2012-10-12
were you able to figure it out?

I created the alias.conf in /etc/modprobe.d/

then I edited the /etc/network/interfaces like this 

auto lo
iface lo inet loopback

auto bond0
iface bond0 inet static
address 192.168.8.177
netmask 255.255.255.0
gateway 192.168.8.254
hwaddress ether 08:00:27:d2:a2:3a
slave bond0 eth0 eth1

reboot

then I get bond0 up with the ip I set, eth0 doesn't get an ip from the dhcp but eth1 does and eth0 eth1 and bond0 have the same MAC address I can't find my mistakes I have tried with 3 different ways and no luck yet..

---

### Post by Rural on 2012-11-09
Best have a closer look at [the example in Stephane's blog post]("http://www.stgraber.org/download/complex-interfaces"). His is pretty much the definitive resource on what you are trying to do in 12.04. What he explains is the opposite of what you've done. And you've got some weird mistakes in your interfaces file that probably aren't helping.

You need something more like the following:

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet manual
   bond-master bond0

auto eth1
iface eth0 inet manual
   bond-master bond0

auto bond0
iface bond0 inet static
    address 192.168.8.177
    netmask 255.255.255.0
    gateway 192.168.8.254
    bond-slaves none
    bond-miimon 100
    bond-mode 802.3ad  #assuming your switch supports it. Something else otherwise.

```

I have played with bonding quite a bit over the last couple of years. It doesn't necessarily perform as you would first expect. (For example, I've never seen performance above the capacity of a single connection between two machines running bonded interfaces (yet!), but if you have multiple machines accessing a single machine with a bonded interface, it definitely works.)

And I'm still having issues with it not starting correctly after a reboot when dealing with bonds of four interfaces.

> **MiLoX said:**
> were you able to figure it out?

I created the alias.conf in /etc/modprobe.d/

then I edited the /etc/network/interfaces like this 

auto lo
iface lo inet loopback

auto bond0
iface bond0 inet static
address 192.168.8.177
netmask 255.255.255.0
gateway 192.168.8.254
hwaddress ether 08:00:27:d2:a2:3a
slave bond0 eth0 eth1

reboot

then I get bond0 up with the ip I set, eth0 doesn't get an ip from the dhcp but eth1 does and eth0 eth1 and bond0 have the same MAC address I can't find my mistakes I have tried with 3 different ways and no luck yet..

---

