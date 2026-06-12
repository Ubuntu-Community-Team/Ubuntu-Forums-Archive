---
title: "help needed to create a &quot;captive portal&quot; with IPTABLES"
date: 2012-10-11
forum: Networking &amp; Wireless
---

### Post by alenis on 2012-10-11
I need help to solve the following problem: I have an Internet site on a PC connected to a DLINK DAP 1360 access point. The PC is not connected to the Internet. I would like that people who connect to the access point, when opening their browsers, were directed to the site residing on the PC automatically, without the need of typing in its address (which is 192.168.0.2).

I did the following:
- I redefined the 404 error page of the web server, which is now the same as the homepage of the site;
- I installed DHCP on the server configuring it like this: 
```

subnet 192.168.0.0 netmask 255.255.255.0 {
    range 192.168.0.60 192.168.0.200;
    option routers 192.168.0.2;
}

```
- finally, I tried in several ways to use iptables to redirect http traffic to port 80 on the server, e.g.  
```

iptables -t nat -A PREROUTING -p tcp -dport 80 -j DNAT --to-destination 192.168.0.2:80

```
I used many variants of that command, but none worked: clients can connect to the access point, they get their local IP address but the browser is not automatically directed to the site.
Can anybody suggest a solution, possibily using the hardware I got?
Thanks

---

