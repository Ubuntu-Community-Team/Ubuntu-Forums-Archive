---
title: "pptp VPN in Karmic"
date: 2009-11-15
forum: Networking &amp; Wireless
---

### Post by shineymart on 2009-11-15
I need to connect to my work network from home using pptp and Karmic on my laptop. Using network manager I set up a VPN connection and can connect and see our internal web app - great!

But.... all my internet traffic is now going down the vpn, which is not so great since my work connection is slower than at home.

So... I checked 'use this connection only for resources on its network' and reconnected - while network manager appears to connect to the VPN ok and my internet connection is OK I can't see anything on the work network at all.

Routes command reveals

Without vpn
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     *               255.255.255.0   U     2      0        0 wlan0
link-local      *               255.255.0.0     U     1000   0        0 wlan0
default         192.168.0.1     0.0.0.0         UG    0      0        0 wlan0

With VPN and 'use this connection only for resources on its network' checked I get
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.9.xxx.xxx   *               255.255.255.255 UH    0      0        0 ppp0
xxxx.xxxxxxxxxx 192.168.0.1     255.255.255.255 UGH   0      0        0 wlan0
192.168.0.0     *               255.255.255.0   U     2      0        0 wlan0
link-local      *               255.255.0.0     U     1000   0        0 wlan0
default         192.168.0.1     0.0.0.0         UG    0      0        0 wlan0

If not I get the following routing
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.9.xxx.xxx   *               255.255.255.255 UH    0      0        0 ppp0
xxxx.xxxxxxxxxx 192.168.0.1     255.255.255.255 UGH   0      0        0 wlan0
192.168.0.0     *               255.255.255.0   U     2      0        0 wlan0
link-local      *               255.255.0.0     U     1000   0        0 wlan0
default         *               0.0.0.0         U     0      0        0 ppp0

The VPN server is using pptp and is dynamically allocating an ip address lease as I log in. 

Thanks in advance

Martyn

---

### Post by shineymart on 2009-11-25
Bump

Anyone?

---

### Post by agibby5 on 2009-12-17
I'm having this same problem.  I had this working Intripid, I think.  My VPN settings broke in Jaunty and I never tried to fix them.  I just got my VPN connection working again on Karmic.  But, like OP, all my traffic is going through the VPN.  The settings in PPTP are different from when I last set this up.  What do I need to do on the IPv4 Settings page to route only work related traffic through the VPN?

---

