---
title: "Ubuntu Server 12.04 + Static IP = NO Internet"
date: 2013-06-25
forum: Networking &amp; Wireless
---

### Post by remush on 2013-06-25
Hi all,

Just installed ubuntu server 12.04 onto computer, everything is working fine, I ran 
sudo apt-get update
sudo apt-get upgrade
with no problems.

Then did some reading to setup a static ip, as this computer is going to be a cups printer server for a training room, with a usb printer attached. And I'll be adding the printer to windows computers via the servers ip address, so I need it to be static.

So Found some help here: [https://help.ubuntu.com/lts/serverguide/network-configuration.html](https://help.ubuntu.com/lts/serverguide/network-configuration.html)

Heres my /etc/network/interfaces file
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
address 10.1.1.201
netmask 255.0.0.0
gateway 10.1.1.1
dns-nameserver 10.1.1.1
```

After making these changes and restarting the computer, I can ping the ip address's of computers on my local network, but can't ping google.com.au anymore. Also running sudo apt-get udpate fails.

I've been looking into this online for a few days now and think I need some help.
10.1.1.1 is the address on our network for the adsl modem that gives us our internet access. Every other computer on the network uses 10.1.1.1 as the gateway address and the dns address, including a few microcore linux file servers.

Suggestions and advice welcome.

---

### Post by remush on 2013-06-25
Solved this, I miss spelled dns-nameserver, it should be dns-nameservers :)

---

### Post by BrunoLotse on 2013-06-25
> **remush said:**
> Solved this, I miss spelled dns-nameserver...:)Hi,It is **misspelled**  ;)))Cheers,Bruno

---

