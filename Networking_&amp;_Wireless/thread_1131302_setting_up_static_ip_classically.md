---
title: "setting up static ip classically?"
date: 2009-04-20
forum: Networking &amp; Wireless
---

### Post by hyperyoda on 2009-04-20
Can someone please tell me how I can setup my new DSL from Speakeasy (Nidhog - a Verizon reseller - no longer does residential DSL so i needed a new ISP) using just static IP (no DHCP) and entering the info manually? Service should be on in 3 days (still waiting for modem and self-install kit to arrive) and I just received this email:

This is the technical information you will need to set up your computer when your DSL circuit is installed.

Your ip address(es) will be:


[ip]


Your gateway will be: ("Router Address" on Macintosh)

66.93.172.1


Your DNS servers will be (in order):

66.92.159.2
216.231.41.2

Your subnet mask is: 255.255.255.0

So what files do I enter this info into and what commands will I type to get the service working and to stop it? I am running Dapper Drake Live CD.

Zach

---

### Post by sisco311 on 2009-04-20
You can use the network manager to setup the static IP.
I think it's installed by default. The icon should be on the top panel's notification area. 

or
assuming that eth0 is your ethernet device:

/etc/network/interfaces should look like this:
```

auto lo
iface lo inet loopback

iface eth0 inet static
address XXX.XXX.XXX.XXX #replace XXX with your ip
netmask 255.255.255.0
gateway XXX.XXX.XXX.XXX 

```

and /etc/resolv.conf:
```
nameserver XXX.XXX.XXX.XXX #replace XXX with the DNS server's ip
nameserver XXX.XXX.XXX.XXX
```


restart the net with:
```
sudo /etc/init.d/networking restart
```

edit the files with:
```
gksu gedit /path/to/file
```

EDIT: POSTING YOUR IP ON A PUBLIC FORUM IS NOT A GOOD IDEA. Edit your post!!!

---

### Post by hyperyoda on 2009-04-20
> **sisco311 said:**
> You can use the network manager to setup the static IP.
I think it's installed by default. The icon should be on the top panel's notification area. 

or
assuming that eth0 is your ethernet device:

/etc/network/interfaces should look like this:
```

auto lo
iface lo inet loopback

iface eth0 inet static
address XXX.XXX.XXX.XXX #replace XXX with your ip
netmask 255.255.255.0
gateway XXX.XXX.XXX.XXX 

```

and /etc/resolv.conf:
```
nameserver XXX.XXX.XXX.XXX #replace XXX with the DNS server's ip
nameserver XXX.XXX.XXX.XXX
```


restart the net with:
```
sudo /etc/init.d/networking restart
```

edit the files with:
```
gksu gedit /path/to/file
```

EDIT: POSTING YOUR IP ON A PUBLIC FORUM IS NOT A GOOD IDEA. Edit your post!!!


Thanks Sisco!

And I edited my post to mask the IP. Good tip :)

---

### Post by lensman3 on 2009-04-21
I have found that Networkmanager has to be disabled.  You are trying to setup a static IP address.  Networkmanager tries to setup a dhcp IP address, from a dhcp server.  Networkmanager will try and take over Network manager and it really screws things up.

You will have to disable Networkmanager with "chkconfig".

Hope this helps.  Networkmanager is not ready for prime time and static IP's.

---

### Post by hyperyoda on 2009-04-21
> **lensman3 said:**
> I have found that Networkmanager has to be disabled.  You are trying to setup a static IP address.  Networkmanager tries to setup a dhcp IP address, from a dhcp server.  Networkmanager will try and take over Network manager and it really screws things up.

You will have to disable Networkmanager with "chkconfig".

Hope this helps.  Networkmanager is not ready for prime time and static IP's.

Thanks.

---

