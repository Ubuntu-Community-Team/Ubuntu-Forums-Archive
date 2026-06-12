---
title: "Internet Connection Problems With Sky Broadband's Cable Modem"
date: 2009-05-15
forum: Networking &amp; Wireless
---

### Post by shinkaide on 2009-05-15
Hello, I'm having trouble using Sky Broadband (provided by SkyCable here in the Philippines) with Ubuntu 8.04.

On startup, Ubuntu detects it and it's recognized and used as "Wired Connection". However, I can't access any website. There's no data going through. I try doing "ping website" but nothing gets through (unknown host).

Help, please?

---

### Post by timcredible on 2009-05-15
you probably need to configure the modem, usually you web into [http://192.168.1.1](http://192.168.1.1) and setup whatever you need with your particular isp, maybe a username/password or a vci/vpi info, or whatever.  ask your isp if you need to configure your modem.  also, make sure the modem is providing dhcp info to your lan.

---

### Post by shinkaide on 2009-05-15
Hi tim. Well, I called up my ISP and they said that the service is of the typical "plug-it-in-and-you're-set" kind. When they set it up on our windows PC here, they just basically plugged it in and it worked (they also told me that I would have to consult a third party with regard to Linux support).

The PC is directly connected to the modem, BTW. Trying to connect to 192.168.1.1 ... nothing doing.

I've tried the same with my Ubuntu box, and while it recognized and automatically selected the connection, I couldn't access anything. I tried the adding following (to set up DHCP, I presume) to my /etc/network/interfaces :

```
auto eth0
iface eth0 inet dhcp
```

but it didn't work either. I've been trying to find something (anything) through the forums, but for now, I'm just kinda stumped.

---

### Post by shinkaide on 2009-08-13
Ummm... just wanted to say that I've managed to solve the problem. Simpler than I thought it was...

Just unplugged the cable modem and then plugged it back in, waited for the connection to be recognized by ubuntu, and then typed the following:

```
sudo dhclient -r
sudo dhclient
```

if it doesn't work the first time, just try it again after a minute or two.

---

