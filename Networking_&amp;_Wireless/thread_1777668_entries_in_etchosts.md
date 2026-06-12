---
title: "entries in /etc/hosts"
date: 2011-06-08
forum: Networking &amp; Wireless
---

### Post by mahmoodn on 2011-06-08
How multiple entries in /etc/hosts work? for example I have these entries:

127.0.0.1     localhost localhost.localdomain
192.168.1.1   mpc
219.32.34.143 mpc mpc.domainname.com

So if someone ping "mpc" what is the correct ip address? also can I write 
127.0.0.1     localhost localhost.localdomain mpc

thanks to anybody who explain that.

---

### Post by webofunni on 2011-06-08
It will take the first entry.

---

### Post by dargaud on 2011-06-08
Take a look [here about DNS search order]("http://www.cyberciti.biz/faq/howto-change-dns-search-order-in-linux/"). Then yes the first (and 2nd if you use IPv6) line should be: 
> 127.0.0.1       localhost.localdomain   localhost
::1     lpsc0174x       localhost6.localdomain6 localhost6
Then you can have additional entries for your own computer (multiple names are fine):
> 127.0.1.1       homeserver   mylinux.dyndns.com
Then you can have static entries for other computers on your local network (in case you don't have DHCP or want to speed things up:
> 192.168.1.3       laptop
Then it's a [very good idea]("http://winhelp2002.mvps.org/hosts.htm") to put fake entries to get rid of add networks (just use 0.0.0.0 instead of 127.0.0.1 like in many of those examples):
> 0.0.0.0  phpadsnew.abac.com
0.0.0.0  a.abnad.net
0.0.0.0  b.abnad.net
...

---

### Post by redmk2 on 2011-06-08
> **mahmoodn said:**
> How multiple entries in /etc/hosts work? for example I have these entries:

127.0.0.1     localhost localhost.localdomain
192.168.1.1   mpc
219.32.34.143 mpc mpc.domainname.com

So if someone ping "mpc" what is the correct ip address? also can I write 
127.0.0.1     localhost localhost.localdomain mpc

thanks to anybody who explain that.

You are correct in having concerns about mapping the name *mpc* to multiple IP addresses.  This is wrong and should never be done.  As @webofunni has said when the map of hostname to IP is made it will take the first one.

But then again what are you trying to achieve?  Since this is a mapping of the [SIZE="3"]*hostname to an IP address *[/SIZE]that others on the LAN side of the network can use to communicate with you, you should use the address that is configured to the NIC that is connected to the network (eht0 or somesuch).  That would be the one in your case that is 192.168.1.1.  I assume that the other valid address is your ISP.  You do not need to name this.  The ISP already has a name mapped.

The IP addresses in the range 127.0.0.0/8 are only available to you locally (every host has this).  You should only map names like localhost or testhost to it.

My etc/host file is like this```
127.0.0.1 localhost 
192.168.1.25 malibu surfrider
```

Malibu is the ***hostname*** and surfrider is an ***alias***.

If you want to map other hostnames to their IP addresses you can do that too.

I map my network printer as ```
192.168.1.200 bb-hp1 printer
```and my router as```
192.168.1.1 bb-gw1 router
```

---

