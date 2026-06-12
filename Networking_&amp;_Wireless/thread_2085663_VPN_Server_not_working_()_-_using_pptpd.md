---
title: "VPN Server not working (?) - using pptpd"
date: 2012-11-18
forum: Networking &amp; Wireless
---

### Post by d3ngar on 2012-11-18
Hi, 

I had to reinstall my system when I upgraded to 12.04.
Unfortunately, although it was previously working, the VPN server isn't working as I wanted.

I followed the guide here: [http://blog.riobard.com/2011/11/12/pptp-vpn-on-ubuntu](http://blog.riobard.com/2011/11/12/pptp-vpn-on-ubuntu)

Sadly I can't connect.

The service is running.
I see that pptpd is listening to port 1723.

The strange thing is: I previously had a ppp virtual network adapter, but this is no longer the case. When I look at ifconfig -a, I just get the network adapter eth0 and the loopback interface. 

Any help would be much appreciated...

Thanks,

Chris

---

### Post by ahallubuntu on 2012-11-18
Isn't there a server logfile you can view for pptpd, so you know what's happening when you try to connect?  I know there is for the OpenVPN server.  I find that very helpful for debugging VPN server installations.

---

### Post by d3ngar on 2012-11-18
> **ahallubuntu said:**
> Isn't there a server logfile you can view for pptpd, so you know what's happening when you try to connect?  I know there is for the OpenVPN server.  I find that very helpful for debugging VPN server installations.
Well, there seems to be some logging issue...

I think the logging should happen in /var/log/wtmp, but the file is empty.

---

### Post by d3ngar on 2012-11-18
Well, I did some installing and installed ufw and added 1723 and 22 to the allowed list. 

Also strange: when I use the command
```
service pptpd status
```
I get no response.

I enabled logging on the firewall and I can see that I'm getting blocked.

```
Nov 19 0   kernel: [15491.072669] [UFW BLOCK] IN=eth0 OUT= MAC=00:XX:25:e4:XX:7d:00:XX:9f:4d:93:76:XX:00 SRC=222.94.138.25 DST=192.168.1.103 LEN=64 TOS=0x00 PREC=0x00 TTL=45 ID=57419 DF PROTO=TCP SPT=58938 DPT=51413 WINDOW=65535 RES=0x00 SYN URGP=0 

```

I can't add the port 1723 to the allowed list, as it's already on there. I obviously restarted the service too.

---

### Post by d3ngar on 2012-11-25
The problem still persists...

Anyone know about pptpd on Ubuntu 12.04?

---

