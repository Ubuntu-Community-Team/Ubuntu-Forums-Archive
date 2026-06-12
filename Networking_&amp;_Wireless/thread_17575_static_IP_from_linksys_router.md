---
title: "static IP from linksys router"
date: 2005-03-01
forum: Networking &amp; Wireless
---

### Post by dstrebel on 2005-03-01
I was wondering if anybody knows how to assign a static ip to a machine from a linksys router.

---

### Post by WillCooke on 2005-03-01
[QUOTE=dstrebel]I was wondering if anybody knows how to assign a static ip to a machine from a linksys router.[/QUOTE]
 The easiest (only?) way is configure your computer to use a static IP address, rather than DHCP.

Have a look at the /etc/network/interfaces file.  

You need something like this:

auto eth0
iface eth0 inet static
        address 192.168.0.100 (an address not in your DHCP pool)
        netmask 255.255.255.0 
        network 192.168.0.0 
        broadcast 192.168.0.255
        gateway 192.168.0.1 (the IP of your router)

---

### Post by mrosenlof on 2005-03-01
You can tell the router to always assign the same IP address given a specific MAC address.  I do this at home, DHCP clients always get the same IP, so I can treat them as if they are static, but when the machines go on the road, they're still set up to get their info from the local DHCP server.

Poke around the Router's administration pages, and you can probably find where to set it.

---

### Post by eli_d on 2005-12-02
my linksys router doesn't give the option to assign static IPs to computers on the local network unless you assign ALL computers on the local network static ips.

it's a bit of a shame... however configuring the one computer manually is fairly simple.

---

### Post by MetalMusicAddict on 2005-12-02
[QUOTE=mrosenlof]You can tell the router to always assign the same IP address given a specific MAC address.  I do this at home, DHCP clients always get the same IP, so I can treat them as if they are static, but when the machines go on the road, they're still set up to get their info from the local DHCP server.

Poke around the Router's administration pages, and you can probably find where to set it.[/QUOTE]
Isnt that only for wireless conections? dstrebel didnt say which kind of connection.

---

### Post by teaker1s on 2005-12-02
check for documentation and firmware from manufacturer as new features are added

---

### Post by claydoh on 2005-12-02
What [I]I do on my befsr41 Linksys router is go to the DHCP tab in the config, and set the starting IP number to something like 192.168.1.200 or something along those lines, just something higher than the address I want to use as a static number. That way I can still use DHCP for anything else plugged in to the router. Then i have my main box set up to 192.168.1.100

from that tab you can disable dhcp altogether if you wish, but you of course will have to set up all the proper info at each system connected, you can't set up a ststic ip from the router itself, it needs to be done at your computer itself
[/I]

---

