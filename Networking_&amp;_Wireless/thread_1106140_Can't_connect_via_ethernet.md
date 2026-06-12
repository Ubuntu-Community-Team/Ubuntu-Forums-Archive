---
title: "Can't connect via ethernet"
date: 2009-03-25
forum: Networking &amp; Wireless
---

### Post by cdawley4 on 2009-03-25
I have a Dell Laptop with ethernet and wireless pcmcia card.  I am trying to connect to the internet via ethernet to get my wireless working.  I have a Linksys WRT54G router.  I installed 8.10 last night.  When I plug in the ethernet cable, it doesn't come back with an IP address.  In the Network Configuration, it is set to DHCP.  What do I need to fill in to get the ethernet to connect to my router?  All I see is the SSID, Mac Address, and some other stuff to fill in.

Thanks,

---

### Post by Anthon on 2009-03-25
Have you checked that the appropriate lights are on on the router and next to the rj45 connector on the Dell? Does the router give out DHCP to other computers, or to this one when running some other OS (version)? 
I seem to remember that some older Dells had special drivers for wired ethernet as well.

---

### Post by arpi_amsterdam on 2009-03-25
Check the basics like do you have a link?

```

rene@rene-lt:~$ sudo ethtool eth2
Settings for eth2:
	Supported ports: [ TP ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Half 1000baseT/Full 
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Half 1000baseT/Full 
	Advertised auto-negotiation: Yes
	Speed: 100Mb/s
	Duplex: Full
	Port: Twisted Pair
	PHYAD: 1
	Transceiver: internal
	Auto-negotiation: on
	Supports Wake-on: g
	Wake-on: d
	Current message level: 0x000000ff (255)
	**Link detected: yes**

```

What do you connect to, to a router? If you know the subnet you configured there, or what the manual tells you to set it to, you can try to set an ip manually:

```

ifconfig eth0 192.168.1.100 netmask 255.255.255.0 

``` 

Then try to ping your gateway 

If this all works out, there is something wrong with the DHCP settings of the network you plug into

---

### Post by cdawley4 on 2009-03-25
Both my desktop and laptop obtain a DHCP address from my router.  My desktop is running WinXP and my laptop was running WinXP, until I changed it over to 8.10 last night.  I do see the link light on the laptop.  Are there any special settings that I need to fill in on the ethernet connections such as SSID and MAC address, or does that matter?  I will try to see if I have a link when I get home.  I am hoping that I don't need to install a separate driver for the ethernet.  If that is so, how would I go about doing it?  I am still a newbie and working with a laptop that the CD Drive doesn't work is a little troublesome.  I have to go between both computers with my flash drive.  I appreciate all the help I can get.

Thanks,

---

### Post by Iowan on 2009-03-25
From what I've read (still on the to-do side of a(n) Ubuntu laptop) laptops and wireless are somewhat tricky. One way to check status is via **sudo lshw -C network**. This should show if the wireless card gets an alias.

---

### Post by arpi_amsterdam on 2009-03-26
Just to make sure, this is a wired ethernet connection we are talking about, right?
If you have no link, that means there is someting low-level the matter. It could be as simple as a bad cable. Please make sure to check that, I will assume it was working when you had XP running. In that case, it might be a driver issue..
What kind of NIC is it? You can get a hardware list with 
```
lspci
```
check if the driver loaded during bootup:
```
dmesg | grep eth
```
But maybe first of all, check the network-manager settings on the panel.

---

### Post by superprash2003 on 2009-03-27
also post output of **ifconfig**

---

