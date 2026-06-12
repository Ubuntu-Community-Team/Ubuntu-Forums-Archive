---
title: "Ports blocked by default"
date: 2011-05-05
forum: Networking &amp; Wireless
---

### Post by sale666 on 2011-05-05
Hello ok here is the problem... as i read every linux distro has ports "open" maybe i read the wrong information but when i connect my machine to the internet its ADSL connected wireless with static ip as:

ip: 192.168.1.20
gateway: 192.168.1.1

on router

NAT-Port forward TCP and UDP on 192.168.1.20 port 28960

there that makes sense but nope it does not work! Why? ubuntu is blocking ports by default?
however if i do nc -l 28960 port is open for like 2 seconds and than closed!

Any ideas? i have tryed everything and been trying to configure this for months :(... cant open a port on ubuntu! :(

---

### Post by eentonig on 2011-05-05
By default, on ubuntu (and I think most linux distributions) all ports are closed for incoming traffic. Or better put, no services are activated that accept external connections.

---

### Post by sale666 on 2011-05-05
> **eentonig said:**
> By default, on ubuntu (and I think most linux distributions) all ports are closed for incoming traffic. Or better put, no services are activated that accept external connections.

ok thank you i tried with 
sudo iptables -A INPUT -p tcp --dport (port number) -j ACCEPT
in my case port number 28960 and passed no problem but when i go to can you see me says connection refused! any advice?

---

### Post by sale666 on 2011-05-05
does any 1 know how o open a port on ubuntu? i have tryed various stuff in iptables rules ect. any 1?

---

### Post by Cheesehead on 2011-05-05
If Ubuntu receives a connection request for a port, it connects the request to the service listening on that port. If no service is listening on that port, than Ubuntu -naturally- refuses the connection.

By default, ports *are* open - try an IPTables dump, and you will see that.
But that doesn't mean any service is listening.

1 ) Use 'netstat -tulpn' to confirm that the the service is really listening on the desired port. If the service isn't listening, check your service's config. 

2) Check that the service isn't hung or frozen. Can you connect to it through the loopback interface?

3) If the service really is active and listening, but you cannot connect from outside, then check your IPTables.

---

### Post by sale666 on 2011-05-05
ok thank you i checked and listen is not on my desired port or ip its not even here and some ports are without listen!

Can you please tell me how to do it?
Thank you!

---

