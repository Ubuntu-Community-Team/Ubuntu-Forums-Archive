---
title: "connect to home pc remotely"
date: 2006-07-14
forum: Networking &amp; Wireless
---

### Post by remsy on 2006-07-14
Hi. I'm behind a firewall and proxy server ( I can only use port 80 or 443) and would like to connect to my ubuntu box via putty (from windows). 

I have ssh server running, but I need to use port 80 or 443 and make my remote computer accessible from anywhere. What are the steps to achieve this?

thanks

---

### Post by mazirian on 2006-07-14
What is being firewalled, the outbound connections from your remote  location or the inbound connections on your home box?  If the former, you may set up [http://www.nocrew.org/software/httptunnel.html]("http://www.nocrew.org/software/httptunnel.html") to accomplish what you want.  It's not exactly trivial, but if you google for that package you will find some howtos.

If it's a firewall at home that you control, you should simply be able to forward port 22 to the local IP address of the box you want to access. You need to configure your router using its web interface if it has one.

Finally, you'll need to know the ip address, obviously, of your home box.  This is likely to be dynamic.  If so, you may use one of the many dynamic IP services that will provide DNS services for you, so you can connect to a name rather than a constantly changing number.  A cron job on your home box would occasionally check your home connection's IP and then update the DNS records at the service.  Checkout [http://www.dyndns.com/](http://www.dyndns.com/) for this purpose.

---

### Post by remsy on 2006-07-14
Yes, it's the firt scenario, the outbound connection is firewalled and I have a dynamic IP at home.

Thanks a lot.

---

