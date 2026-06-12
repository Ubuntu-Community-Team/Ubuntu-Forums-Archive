---
title: "Access my LAN web server using dyndns?"
date: 2009-09-21
forum: Networking &amp; Wireless
---

### Post by CyberAngel on 2009-09-21
Hi,

I have a home server for my personal needs. On that server I`m initiating my adsl connection using pppoe to be able to handle all the traffic from the internal interfaces to the internet (the virtual ppp0 interface) and I`m also using a dyndns cause I have a dynamic IP. I`m also running a vmware server 2 with some virtual machines on it.
One of the virtual machines that I`m running is another ubuntu server setup to be used as a web server.

I want to be able to view the web server on the virtual machine both from my LAN and the internet if I use my dyndns. Is it possible?

I can access my web server from my LAN if I use it`s internal ip and from the outside world using the dyndns name, if I add an iptable rule in the nat table so that every request is coming in my ppp0 device port 80 is being redirected on the internal ip of the web server (the virtual machine).
The problem is that if I use my own dyndns name from within my LAN, I get a request timed out.

Thanks

---

### Post by badger_fruit on 2009-09-21
What happens if you PING or TRACEROUTE your DYNDNS from a local machine?

---

### Post by CyberAngel on 2009-09-21
It shows that the external dynamic ip is replying correctly.

If I traceroute the dyndns there is only one hop to the external ip that this is reasonable cause only a switch exists between my computer and my home server.

---

### Post by badger_fruit on 2009-09-21
This sounds like a problem we have here at work that I've not been able to figure out!
If we try to access the websites we hold here from inside of the LAn using the external IP or DNS, it times-out; if we try from outside the LAN then it works.  Ever so strange!

I'm out of ideas here though, sorry but I hope you find a solution!

---

### Post by CyberAngel on 2009-09-21
> **badger_fruit said:**
> This sounds like a problem we have here at work that I've not been able to figure out!
If we try to access the websites we hold here from inside of the LAn using the external IP or DNS, it times-out; if we try from outside the LAN then it works.  Ever so strange!

I'm out of ideas here though, sorry but I hope you find a solution!

Somehow we should redirect the requests coming from the internal network to the external ip, again into the internal network to the correct ip address but I don`t know the way to do it.

---

