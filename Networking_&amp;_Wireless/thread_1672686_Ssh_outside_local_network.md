---
title: "Ssh outside local network"
date: 2011-01-21
forum: Networking &amp; Wireless
---

### Post by psycho5 on 2011-01-21
Hi

If i want to use SSH to log on to my home computer, which is connected to the router, how do I go about connecting to it?

If I get my external IP of the computer at home, it will show me the external IP of the router correct? Then I need to forward the router's external IP to my computer at home. But then, how do I connect using ssh?

ex:

ssh user@routerexternalip 

or do I need to consider my local IP of the computer at the router's network?

---

### Post by gmargo on 2011-01-21
You need to configure your router to do "port forwarding".  Then traffic coming in on that TCP port is forwarded through the router to your internal ssh server machine.  The router will take care of NAT as usual.

Rather than using the default ssh port 22, you should consider using a obscure port number.  You can configure your internal ssh server to listen on multiple port numbers, so you can still use port 22 internally.

---

### Post by smurphy_it on 2011-01-21
A port knocking application can be setup for the paranoid.  I haven't used them myself, so I can't comment on how good/bad they are.

---

### Post by psycho5 on 2011-01-21
> **gmargo said:**
> You need to configure your router to do "port forwarding".  Then traffic coming in on that TCP port is forwarded through the router to your internal ssh server machine.  The router will take care of NAT as usual.

Rather than using the default ssh port 22, you should consider using a obscure port number.  You can configure your internal ssh server to listen on multiple port numbers, so you can still use port 22 internally.

Thank you for the reply. So in other words, I configure my router to forward the incomming traffic (external ip) to my ssh server (local machine ip) ? And yes, I know how to use an obscure ssh port. Thanks for that tip.

---

### Post by smurphy_it on 2011-02-14
Yes exactly right.  You can also mess around with Dynamic DNS so you don't have to remember your IP address.  There are a few of them out there, such as dyndns, no-ip, etc...

[http://www.dyndns.com/](http://www.dyndns.com/)
[http://www.no-ip.com/](http://www.no-ip.com/)

If you have dd-wrt or openwrt on your router (linux firmware) it can auto-update it for you, just make sure to have the hostname in there too!

---

### Post by dolphy on 2011-02-23
> **smurphy_it said:**
> Yes exactly right.  You can also mess around with Dynamic DNS so you don't have to remember your IP address.  There are a few of them out there, such as dyndns, no-ip, etc...

[http://www.dyndns.com/](http://www.dyndns.com/)
[http://www.no-ip.com/](http://www.no-ip.com/)

If you have dd-wrt or openwrt on your router (linux firmware) it can auto-update it for you, just make sure to have the hostname in there too!

If you don't want to use those dynamic IP services, I wrote a simple Python script that will email (using a Gmail account) you with your new IP address if it changes.  It uses Python and MySQL.  I have it scheduled to run every hour.  I know it's probably not as good as the solutions mentioned above, but I like to mess around with Python so I rolled my own solution.  Eventually I'll extend it to store a history of the past IPs, etc.

Let me know if anyone wants it.  I'd be happy to share.

---

### Post by LMelior on 2011-02-23
Can someone help me with the last step?

Here's my problem: I can ssh in to my DD-WRT router, but I can't directly reach the machine behind it.  I have DD-WRT set up to forward traffic it gets on (let's say) port 23456 to port 22 on the machine I want to reach.

Now here's the weird part:  if I do "ssh -p 23456 [email]user@domain.com[/email]" from within my network, it works.  If I do the exact same from outside, nothing happens -- no response.

But like I said, I can reach the router itself from outside.  I can do a double hop (ssh to router, then to machine), but I don't think I can forward X that way because my router doesn't understand the ssh -X option.

---

### Post by gmargo on 2011-02-23
> 
I have DD-WRT set up to forward traffic it gets on (let's say) port 23456 to port 22 on the machine I want to reach.
I think that should work, but I do it differently: I forward port 23456 to the destination machine without changing the port number.  Then configure **sshd** to listen on both port numbers, so you can still use port 22 internally.  Don't know if this will help, but it's something to try.

Just add the additional port number to /etc/ssh/sshd_config:
```

# What ports, IPs and protocols we listen for
Port 22
Port 23456

```

---

