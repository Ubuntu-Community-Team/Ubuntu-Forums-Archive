---
title: "PPTP VPN Troubles (need help setting it up)"
date: 2013-03-09
forum: Networking &amp; Wireless
---

### Post by Zukaro on 2013-03-09
I'm trying to set up a PPTP VPN server but I'm unable to connect.  I've forwarded port 1723 and enabled PPTP Pass Through on the router.  In Ubuntu I've set everything up following this [guide]("http://www.larmeir.com/2010/03/setting-up-a-pptp-vpn-server-on-debian-and-ubuntu/") (other than the bit about using bind9 as all my IP addresses are static).  I'm not sure what I'm missing.

When I try ```
netstat -anp | grep pptpd 
``` this is what I get:

```
tcp        0      0 0.0.0.0:1723            0.0.0.0:*               LISTEN      1263/pptpd
unix  2      [ ]         DGRAM                    9847     1263/pptpd

```

It appears to be listening on the wrong port, but I'm not sure how to change that.
As for the IP address listed in pptpd.conf, this is what I have:

```
localip 192.168.3.1
remoteip 192.168.5.2-10

```

This should be correct (the reason the remoteip is on 192.168.5.2 rather than .4.2 is because I already have another network running on there, but I can change the IP of that network easily if needed).

---

### Post by Zukaro on 2013-03-12
Does anyone have any ideas as to what the problem might be?  I've looked  around on Google for at least 5 hours the other day and I've yet to  find anything about the issue.

---

### Post by Zukaro on 2013-03-17
Anyone?

---

### Post by Idzi on 2013-09-07
Hi Zukaro, did you ever get this sorted out?  

If not, I think I can help as I have just got a very similar PPTP VPN working on two Raspberry Pis (running the standard Debian based distro). 

Personally, I followed this tutorial more-or-less verbatim and it has worked for me each time:

[http://raspberrypihelp.net/tutorials/21-pptp-vpn-server-raspberry-pi](http://raspberrypihelp.net/tutorials/21-pptp-vpn-server-raspberry-pi)

It is very similar to the tutorial you link to in your first post and is perhaps even based on it.  But the instructions are slightly better explained and there are a couple more steps.  

I would also add that on both occasions I have setup a VPN using this method, I have had to reboot the system as a final step to get it working. (I won't pretend to know why..)

Anyway, I hope this helps.

---

