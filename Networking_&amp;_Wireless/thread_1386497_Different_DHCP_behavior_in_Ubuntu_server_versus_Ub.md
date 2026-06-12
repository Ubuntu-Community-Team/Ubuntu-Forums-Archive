---
title: "Different DHCP behavior in Ubuntu server versus Ubuntu desktop"
date: 2010-01-20
forum: Networking &amp; Wireless
---

### Post by Overvoltage on 2010-01-20
I've noticed something strange in the behavior of how Ubuntu server obtains it's IP address versus Ubuntu desktop and other versions of linux and Windows.  When Ubuntu desktop obtains an IP address from my router that address is retained from one bootup to the next, same behavior as Windows, SuSE, and pretty much any other OS.  Ubuntu server on the other hand grabs a different IP address everytime it boots.  At first I guessed it was a difference in /etc/dhcp3/dhclient.conf so I replaced it with the dhclient.conf from Ubuntu desktop but no dice, it still grabs a new address every time.  

I've noticed some other differences also:  
In /etc/network/interfaces Ubuntu server defines the loopback interface and primary network interface, just as it should but Ubuntu desktop does not define the network interface, only the loopback interface.  I'm guessing something else controls does this.
Desktop appears to be storing previous IP lease information in /var/lib/dhcp3/dhclient.eth0.leases but server doesn't, /var/lib/dhcp3/dhclient.leases is always empty and there's no other files in /var/lib/dhcp3/.  Apparently something isn't writing old lease info there. 

Without setting a static IP address, how can Ubuntu server be configured to retain the same IP address between boots like Ubuntu desktop?

I'm using Ubuntu server 8.04LTS, Ubuntu desktop 9.10 & 9.04, SuSE 11.0, Linux Mint, Windows XP, pfSense 1.2.2 as router.

Thanks...

---

### Post by chili555 on 2010-01-20
I would think a static address is the only reasonable way to set up a server. Why wouldn't you want to do so? 

Networking is generally controlled by Network Manager on desktop machines. Since it's a GUI-oriented system, it's not used on servers. Hence the subtle differences.

---

### Post by Overvoltage on 2010-01-20
There's a number of reasons I don't want to use a static IP, for instance if I take it to another location with a different network I don't want to hassle with changing the IP, and there are others.  

I figured Network Manager would be involved, but Ubuntu desktop obtains an IP address before anyone logged in.  I don't know if it obtains an address before X starts up or not.  If it does there must be a component of Network Manager which isn't GUI.  

SuSE uses some other method, both desktop and server behave as expected.  I haven't investigated how yet.

---

### Post by Iowan on 2010-01-20
> **Overvoltage said:**
> Without setting a static IP address, how can Ubuntu server be configured to retain the same IP address between boots like Ubuntu desktop?Configure the DHCP server (router) to issue a static lease - based on MAC address. It should be outside the DHCP lease range.

---

### Post by Overvoltage on 2010-01-20
> **Iowan said:**
> Configure the DHCP server (router) to issue a static lease - based on MAC address. It should be outside the DHCP lease range.

This does work but it's a workaround.  Thanks for the suggestion, I might have to go with it.

---

### Post by Overvoltage on 2010-01-21
OK, figured it out finally by reading the dhclient.conf documentation more thoroughly. RTFM is always a good idea. :)

Ubuntu server 8.04 comes with a sample dhclient configuration file named /etc/dhcp3/dhclient.conf-dist.  To configure dhclient in Ubuntu server 8.04 operate as expected, that is retain it's previous IP address and return it's hostname to the dhcp server do the following:

Go to /etc/dhcp3
Backup dhclient.conf by renaming it to dhclient.conf.old or whatever you please
Rename dhclient.conf.dpkg-dist to dhclient.conf
Using your favorite text editor edit dhclient.conf and find an entry named '#reboot 10;'
Remove the # so the line reads 'reboot 10;'
Save the file, exit the editor, and reboot.

Ubuntu server should now retain the IP address it now recieves from the DHCP server.

Questions, comments, flames?

---

### Post by pricetech on 2010-01-21
> **Overvoltage said:**
> This does work but it's a workaround.  Thanks for the suggestion, I might have to go with it.

It's the only way you'll always have the same IP on the server when you're on your network.  Granted, if it tries to renew with your router, it will probably get the same IP assuming there's not a lot of activity on your network, but when you return from having hooked up to someone else's network, you probably won't get the same IP if it's not reserved by your router.

---

### Post by Iowan on 2010-01-21
There are a couple of threads (but I don't have links) that asked about having a machine request a specific IP address via dhclient... but I don't recall if the option exists.

---

### Post by Overvoltage on 2010-01-21
> **pricetech said:**
> It's the only way you'll always have the same IP on the server when you're on your network.  Granted, if it tries to renew with your router, it will probably get the same IP assuming there's not a lot of activity on your network, but when you return from having hooked up to someone else's network, you probably won't get the same IP if it's not reserved by your router.

Perfectly correct.  My main concern was to reduce unnecessary IP address changes and create the same behavior as Ubuntu desktop and other operating systems.

---

### Post by Overvoltage on 2010-01-21
> **Iowan said:**
> There are a couple of threads (but I don't have links) that asked about having a machine request a specific IP address via dhclient... but I don't recall if the option exists.

Interesting, it might be possible to hack dhclient a bit to request a specific address since it has to store the previous IP address between boots.  I'll have to read more about dhclient.

---

