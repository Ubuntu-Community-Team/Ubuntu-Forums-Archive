---
title: "can't connect to network"
date: 2013-01-03
forum: Networking &amp; Wireless
---

### Post by p2ranger on 2013-01-03
I am in the middle of reinstalling Ubuntu Server 12.04. After the installation I was able to ssh in to begin doing things. After I rebooted, I could no longer ssh in. The server also is not able to see anything on the network. The switch has the lights on that are supposed to be there.

 Things I did before rebooted included changing it to a static updates and upgrades,IP address, installed a priter via CUPS, partitioned, formatted, and mounted two additional hard drives.

I am using the exact same contents for my /etc/network/interfaces file. Here are the contents. I can't figure out what I did wrong:

```

auto lo
iface lo intet loopback


auto eth0
iface eth0 inet static
        address 192.168.1.120
        netmask 255.255.255.0
        gateway 192.168.1.1



```

There's also some commented lines in there.

It was working before, I don't know what changed

Thanks for any help

Jason

---

### Post by p2ranger on 2013-01-03
Got it to see the network. I can ping and ssh again. I forgot that I have it hooked into another ethernet port. Change eth0 to eth1

Now it doesn't want to see outside the network.

Any ideas?

Thanks

Jason

---

### Post by spynappels on 2013-01-03
Do you have any entries for the other network card in /etc/network/interfaces? Or are you only using one of your 2 NICs?

What have you tried to do to check outside connectivity? Have you pinged google.com? Have you pinged 8.8.8.8?

Is your router allowing the traffic through? You can check this using traceroute.

---

### Post by Bucky Ball on 2013-01-03
*Thread moved to **Networking & Wireless***

---

### Post by p2ranger on 2013-01-03
Got it working. I wound up reinstalling so I could see where things changed. Discovered I needed to add DNS to my /etc/network/interfaces file.

It seems since my last server install, 10.04, the /etc/resolv.conf file is no longer the place where you list dns for 12.04  It is now listed in the interfaces file with the ip address, gateway, etc. I just listed my router's IP as my DNS

This is what is frustrating about Linux to me, places get changed and all the notes I take on how I set up my server previously become useless. I guess its all in the name of progress somehow.

so now my /ect/network/interfaces file reads:

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth1
iface eth1 inet static
        address 192.168.1.120
        netmask 255.255.255.0
        gateway 192.168.1.1
        dns-nameservers 192.168.1.1

```

Reference:
[http://www.howtoforge.com/perfect-server-ubuntu-12.04-lts-apache2-bind-dovecot-ispconfig-3-p3]("http://www.howtoforge.com/perfect-server-ubuntu-12.04-lts-apache2-bind-dovecot-ispconfig-3-p3")

I have two NICs in my server. eth0 is a 10/100 card and eth1 is a gigabit card. eth0 is not connected

Thanks for bouncing ideas for me

Jason

---

### Post by spynappels on 2013-01-03
Yeah, that got me too when I first moved to 12.04 LTS server, but I guess it makes sense having all the info in one place. Glad you got it sorted though.

---

