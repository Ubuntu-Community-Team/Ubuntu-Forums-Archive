---
title: "Can ping in, canot ping out"
date: 2008-12-30
forum: Networking &amp; Wireless
---

### Post by cov on 2008-12-30
When I run 'dhclient -d eth0' on my Ubuntu Box I get the following:

```
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 1
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

If I set my /etc/network/interfaces to:
```
auto eth0
iface eth0 inet static
address 192.168.0.119
netmask 255.255.255.0
broadcast 192.168.0.255
gateway 192.168.0.1
```

If I then run '/etc/init.d/networking restart' then 'ifconfig' lists my eth0 interface correctly including the IP. 

I can ping the machine from another machine on the network, but cannot that machine from the Ubuntu box.

If this was a windows machine I would say it's a firewall issue...

---

### Post by nzadLithium on 2008-12-30
first off if your using dhcp

try sudo dhclient eth0

(since ur device is eth0, atm from what u were doing it was trying to configure ath0 :p)

try pinging then, see what happens :)
(you'll prob need to find out what ur ip is XD if u didnt know already, ifconfig is the command to use :D).

---

### Post by cov on 2008-12-31
Damn, sorry, that was a typo. It should be 'eth0'.

Sorry for that red herring. As the machine cannot connect I am having to transpose error messages.

In any case, I think that the problem must be hardware related as I cannot connect using a livecd either.

Thanks for the help.

---

### Post by Iowan on 2008-12-31
I've seen a couple of threads where turning off **acpi** helped (pci=noacpi on kernel line in /boot/grub/menu.lst).

---

