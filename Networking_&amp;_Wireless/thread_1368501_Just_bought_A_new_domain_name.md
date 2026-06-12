---
title: "Just bought A new domain name"
date: 2009-12-30
forum: Networking &amp; Wireless
---

### Post by husskii on 2009-12-30
Hi I have just bought a domain name and have installed ISPConfig 3, phpmyadmin, squirrelmail pretty much a LAMP server with a few extras, now the trouble Im having id trying to add my new domain to my webserver so that when u browse to the url it directs you to my website. I tried editing the /etc/network/interfaces and made it look like this.
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
#allow-hotplug eth0
#iface eth0 inet dhcp
auto eth0
iface eth0 inet static
        address 192.168.0.100
        netmask 255.255.255.0
        network 192.168.0.0
        broadcast 192.168.0.255
        gateway 192.168.0.1
```

and also edited my /etc/hosts to 
```
127.0.0.1       localhost.localdomain   localhost
192.168.0.100   server1.example.com     server1

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

but still when u browse my url it still leads u to the company I registered it with, or comes up unknown. Now Im not using the IP that shows when u ping my domain name, and as Im think I should be using it, Im not sure where to add it, because I think if i use the ip for my domain name instead of my actual Ip at home, I wont beable to connect to the net at all..

I was wondering if anyone can maybe advise me on how to do this or point me to a tutorial that might help me, I have vigorous searched on the internet for the last 6hr, maybe even longer and all my searches have come up empty handed, and as this is the first time I have every done this or bought a domain, I dnt even know if Im doing a proper search as I dnt know what Im  ment to be searching for.

help would be greatly appreciated as I am entering into the unfamiliar territory here...

Thanks in advance
Husskii

---

### Post by falconindy on 2009-12-30
Have you registered the domain name with a nameserver host?

---

### Post by husskii on 2009-12-31
hi falconindy yes I have registered the domain.
not I just need my domain name to point to my url.'
I tried entering my rounter IP in my control panel but that just took me to my router setup when u browsed my url lol..
So I think Im a little closer to reaching my goals.
I have now edited that to my local ip instead and currently reinstalling the server, so Ill see how it goes, but I believe it cant just be that simple and I must cofig my network setting on the router maybe.. 
Im not too sure, but I hope I eventually get to my destination..

happy new year!!!

---

### Post by ratcheer on 2009-12-31
Can you ping your new domain from another, unrelated host? Sometimes, it takes a while for a new domain to become "known" by primary DNS in the Internet.

Tim

---

### Post by husskii on 2010-01-17
hi ratcheer that was the problem I just had to wait for it to be known :)

thanks

---

### Post by ratcheer on 2010-01-17
Excellent. You are welcome.

Tim

---

