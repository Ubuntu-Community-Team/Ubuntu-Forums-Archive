---
title: "broken networking/interfaces"
date: 2009-12-21
forum: Networking &amp; Wireless
---

### Post by trstn on 2009-12-21
Ok, I realise this is pretty out there as a help request, but here goes.

I know this is down to networking/interfaces, I remember having this issue once before but I can't for the life of me remember what was wrong.

Basically an automatic upgrade of an ebox-network package has overwritten my network/interfaces file somehow, and now I can't get online, or connect to the box. Clever guy that I am I don't have a backup of the file.

Essentially... eth0 is the external connection coming in.
eth1 is the internal lan, which connects to the net via eth0 (that's all handled by ebox).

Can anyone see anything obviously wrong with the code below? I'm almost certain it's something missing but just can't remember.


```
auto lo eth0 eth1
iface lo inet loopback
iface eth0 inet static
        address 217.113.173.74
        netmask 255.255.255.248
        broadcast 217.113.173.79
        gateway 217.113.173.73

iface eth1 inet static
        address 192.168.1.1
        netmask 255.255.255.0
        broadcast 192.168.1.255
        gateway 192.168.1.1
```

Thanks for any help.

---

### Post by Iowan on 2009-12-21
> **trstn said:**
> 
```
iface eth1 inet static
        address [COLOR="Red"]192.168.1.1[/COLOR]
        netmask 255.255.255.0
        broadcast 192.168.1.255
        gateway [COLOR="Red"]192.168.1.1[/COLOR]
```

Thanks for any help.Somehow, this doesn't look right. If I recall correctly  from other threads - the gateway becomes the default gateway, and there should be only one.

---

### Post by trstn on 2009-12-22
So do I delete the address line or gateway?

Actually, I'm being lazy. I'll try removing one at a time and see what happens when I restart networking.

Fingers crossed, and thanks.

---

### Post by Iowan on 2009-12-22
Delete the gateway (the 192.168.1.1 version).
Good luck!!! :P

---

### Post by ant2ne on 2009-12-22
> **trstn said:**
> 
```
auto lo eth0 eth1
iface lo inet loopback
iface eth0 inet static
        address 217.113.173.74
        netmask 255.255.255.248
        broadcast 217.113.173.79
        gateway 217.113.173.73

iface eth1 inet static
        address 192.168.1.1
        netmask 255.255.255.0
        broadcast 192.168.1.255
        gateway 192.168.1.1
```
Don't delete the gateway. change the address to 192.168.1.111 and then...
```
sudo ifconfig down
sudo ifconfig up
```See if it restores networking. 

This is an interesting interfaces file. You have a complex netmask for eth0, is this a gateway to a ISP?

---

### Post by trstn on 2009-12-27
That's right, we get our incomming connection via WAN, eth0 is the settings relevent to that.

Your fix worked, so thanks greatly, however not without one more thing, turned out I needed a network in my eth0 to get eth1 working correctly.

My fix:

iface eth0 inet static
        address 217.113.173.74
        netmask 255.255.255.248
        **network 217.113.173.75**
        broadcast 217.113.173.79
        gateway 217.113.173.73

Thanks so much for your help, taken me a hella long time to figure that out. Was almost in a heap of trouble :)

---

### Post by ant2ne on 2009-12-28
> iface eth0 inet static
address 217.113.173.74
netmask 255.255.255.248
**network 217.113.173.75**
broadcast 217.113.173.79
gateway 217.113.173.73that network doesn't look right. I don't feel like crunch the numbers right now. So if you have problems with eth0, start troubleshooting there. And/Or reply here.

---

### Post by slakkie on 2009-12-28
> **ant2ne said:**
> that network doesn't look right. I don't feel like crunch the numbers right now. So if you have problems with eth0, start troubleshooting there. And/Or reply here.

It is this network: 217.113.173.72/29 (so it need to be .72)

BTW, you only need:

broadcast, subnetmask, ip and gateway. The network entry can be wiped, since it is redundant (can be figured out by broadcast + subnetmask).

---

### Post by Charlietje on 2009-12-28
You can only have one gateway and it will be the one from 217.113.173.73

A gateway is when your pc cannot find the address or hostname on the local network, it then tries to find it from the gateway.
So if you want to go to the internet, it will not be able to go outside the network from eth1. So delete that gateway, so when you want to go on the internet it will go through eth0

---

