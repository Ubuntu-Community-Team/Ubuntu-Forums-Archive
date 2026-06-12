---
title: "setting up a static ip in  mythbuntu 10.10"
date: 2010-11-19
forum: Mythbuntu
---

### Post by benlyboy on 2010-11-19
Hi all

I need to set a static ip on my mythbox. 

I had to reinstall the whole thing so I moved up to 10,10 

In my last install there was a network manager to use to set up an ip, this seems to be missing from 10.10 so how do i go about setting a static ip?

thanks for any help

---

### Post by ian dobson on 2010-11-20
Hi,

Just edit the interfaces file:-

/etc/network/interfaces
```
auto lo
iface lo inet loopback

#On board RTL adapter
auto eth0
iface eth0 inet static
address 192.168.0.4
netmask 255.255.255.0
gateway 192.168.0.254

#Intel PCI adapter
auto eth1
iface eth1 inet static
address 192.168.0.3
gateway 192.168.0.254
netmask 255.255.255.0
```

You'll need to manually configure the name (ethX) and the ip parameters to match your hardware/network.

Regards
Ian Dobson

---

