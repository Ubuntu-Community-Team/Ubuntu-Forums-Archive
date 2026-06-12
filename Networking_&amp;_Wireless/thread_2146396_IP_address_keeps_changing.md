---
title: "IP address keeps changing"
date: 2013-05-18
forum: Networking &amp; Wireless
---

### Post by psionman on 2013-05-18
Hi

I'm new to networking and I need some help

I've set up [BubbleUPnP Server]("http://www.bubblesoftapps.com/bubbleupnpserver/") but every time I re-boot it gets assigned to a different IP address. I've been through the menus and cannot find any way to fix it. Is there a general way that it might be assigned to a fixed address?

---

### Post by sanderj on 2013-05-18
What kind of IP address? If you mean private, so 192.168.x.y or 10.x.y.z, your router/modem gives your system that IP address. You could lock the IP address in your Ubuntu, but that is risky. Probably better to go into your router/modem's webgui, and lock the IP address there.

---

### Post by psionman on 2013-05-20
Thanks Sanderj
I have a Linksys WRT45G and I don't think they handle statis IP addresses

---

### Post by AmbiguousOutlier on 2013-05-20
Goto 192.168.1.1 in your browser

Is there anything in advanced settings/setup to do with DHCP? You should be able to assign a private IP to the MAC address of your device. 

Or you could do it within Ubuntu which I do, which does work most of the time for me.

in terminal>

```
sudo nano /etc/network/interfaces
```

change 

```
auto eth0
iface eth0 inet dhcp
```

to

```
auto eth0
iface eth0 inet static
        address 192.168.1.100
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.1
```

```
sudo /etc/init.d/networking restart
```

This should work but like Sanderj try the router first.

---

### Post by psionman on 2013-05-24
Thanks for the information

I attach screen dumps of the BubbleUPnP server control page - I can't see a MAC here, so I don't know what to do

and the Router page, is this the right page for setting the fixed IP address, and what should I do?

---

### Post by psionman on 2013-05-29
Bump :)

---

### Post by steeldriver on 2013-05-29
I don't think the WRT54G supports that type of DHCP address reservation on a per-MAC basis - however since you can set its DHCP pool start address (default is 192.168.1.**100 **as you can see in your pic), as long as you choose numbers below that (and obviously make sure you don't create duplicates) you can use any address in the range 192.168.1.2 - 192.168.1.99 as true static addresses set via the Network Manager IPV4 Settings tab (or via /etc/network/interfaces if you are not using Network Manager)

---

