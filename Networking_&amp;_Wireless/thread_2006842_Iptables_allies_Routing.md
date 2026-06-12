---
title: "Iptables allies Routing"
date: 2012-06-19
forum: Networking &amp; Wireless
---

### Post by WindMagi on 2012-06-19
I have a Ubuntu 10.04 Server.

I have 2 public IPs on eth0.  (The second is an allies eth0:0)

I understand that iptables does not support allies.

My goal is to take port 80 based on the incoming address and redirect to a different port on the same server, based on the public IP.

Currently I have not been able to figure out how to do this.

Thanks for any help!

---

### Post by WindMagi on 2012-06-19
Ok, so I figured out the solution.  I will post it just in case it helps anyone else.

I used the following iptables tules to route the http and https to two different glassfish domains based on the public ip on the same server.

iptables -t nat -A PREROUTING -d [PUBLIC IP HERE] -i eth0 -p tcp --dport 80 -j REDIRECT --to-port 8080
iptables -t nat -A PREROUTING -d [PUBLIC IP HERE] -i eth0 -p tcp --dport 443 -j REDIRECT --to-port 8181

iptables -t nat -A PREROUTING -d [Another PUBLIC IP HERE]  -i eth0 -p tcp --dport 80 -j REDIRECT --to-port 8282
iptables -t nat -A PREROUTING -d [Another PUBLIC IP HERE]  -i eth0 -p tcp --dport 443 -j REDIRECT --to-port 8383

If I find this has any errors and/or does not work, I will try to remember to update the post.

---

