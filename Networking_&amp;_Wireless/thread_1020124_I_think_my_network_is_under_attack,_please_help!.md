---
title: "I think my network is under attack, please help!"
date: 2008-12-23
forum: Networking &amp; Wireless
---

### Post by transmition on 2008-12-23
Now, before I describe *what* I did, I think you ought to know *why* I did it.

I have DSLinux on my Nintendo DS, and in order to connect to the internet, it requires that a network either be WEP or unprotected, unprotected causing less problems.

However, over the course of the day, I noticed that under the firewall log, I was seeing a message alike to:
```
Tues Dec 23 17:40:04 2008 1 Blocked by DoS protection 192.168.2.53
```

This made me a little nervous, seeing as my IP was 192.168.2.2. So I go in to change my settings and low and behold, I get the message:
```

Duplicate Administrator

A user at (192.168.2.53) is currently managing the router.

```

Well, this made me very nervous, and I unplugged the router at 17:51. Now however, when I look at the log, (while plugged into ethernet) I see:

```

Tues Dec 23 18:03:33 2008 1 Blocked/RST by DoS protection 85.190.0.3 

```

The other IP that I saw earlier was 65.114.168.238. According to GeoIP, I have people in Arlington Virgina as well as germany attempting to access my router.

Not sure if this is the best place for this post, but could someone explain what is going on?

Using GeoIP,

---

### Post by pdtpatrick on 2008-12-23
lol did you leave your router open? understand that WEP can be cracked in about 5 to 10mins so you might want to use mac filtering on your network to get that going. 

Also since this happened, use a monitoring system like airmon-ng to see who is sending lots of packets or listening on your network.

---

### Post by transmition on 2008-12-23
No, the network is not open, it is back on WPA. I also changed all the passwords.

Does it seem that someone is trying to gain access?

---

### Post by abn91c on 2008-12-23
change the router password, the default for all linksys for instance is admin so anyone can figure it out, also change the router name, do not use linksys as part of the name. you can use any name you want and yes someone did access your network you can also setup mac address filtering on the router

---

### Post by ziesemer on 2008-12-23
> **transmition said:**
> No, the network is not open, it is back on WPA. I also changed all the passwords.

Does it seem that someone is trying to gain access?

It is less likely that someone is intentionally and personally attempting to gain access to your router.  It is more likely that you're being attacked by automated botnets, etc. - and it at least appears that the firewall/router is currently doing its job by blocking the connections.

I don't see that you mentioned what you were using for a firewall/router.  You may have options that you can use lessen potential threats.  Ensure that you have any remote administration services externally disabled, and preferably from the wireless network as well.  Disable any externally-visible ports that aren't needed, as well as other standard security practices that can be found described on numerous sites across the Internet.

---

### Post by transmition on 2008-12-24
Well, the main thing that worried me was when I got an error on my router stating that someone else was administrating it at the same time I was.

Is there any way of blocking the IPs?

Also, could someone elaborate on the use of airmons-ng? When I type:
```
sudo airmon-ng start eth1
```
I get
```

Interface	Chipset		Driver

eth1		UNKNOWN		wl (monitor mode enabled)

```

I am not sure where to go from there.

In Addition:

Looking at my routers log again shows me something rather strange, being that my IP address is being showed as connecting at times when my laptop is powered off:
```

Tues Dec 23 21:00:21 2008 - WAN DHCP Client Connected IP MyIPAddress
Tues Dec 23 22:00:25 2008 - WAN DHCP Client Connected IP MyIPAddress
Tues Dec 23 22:41:37 2008 - WAN DHCP Client Connected IP MyIPAddress
Tues Dec 23 23:43:29 2008 - WAN DHCP Client Connected IP MyIPAddress
Wed Dec 24 00:44:44 2008 - WAN DHCP Client Connected IP MyIPAddress
Wed Dec 24 01:47:17 2008 - WAN DHCP Client Connected IP MyIPAddress
Wed Dec 24 02:48:30 2008 - WAN DHCP Client Connected IP MyIPAddress
Wed Dec 24 03:51:04 2008 - WAN DHCP Client Connected IP MyIPAddress
Wed Dec 24 04:52:16 2008 - WAN DHCP Client Connected IP MyIPAddress
Wed Dec 24 05:54:52 2008 - WAN DHCP Client Connected IP MyIPAddress  

```

Could there be something faulty with the router?

---

### Post by ziesemer on 2008-12-24
It is rather difficult to answer many of these questions without knowing what your router is.  Is it a typical Linksys/D-Link/Netgear/etc. off-the-shelf router?  Does it have an alternate firmware installed?  Is it another Linux box?  Or something else?

---

### Post by transmition on 2008-12-24
It is a D-Link F5D7230-4 6000, running firmware version F5D7230-4_US_8.01.07

---

