---
title: "How to Build a FTP Server behind Gateway"
date: 2009-09-01
forum: Networking &amp; Wireless
---

### Post by Abu Hauna on 2009-09-01
Dear Ubuntuers,

How to create rule in iptables or another method (gateway computer) if I want to setup an local ftp server. The ftp server should be access from external (internet) pass through by gateway. Gateway has also ip public.
Example :
Gateway ip : 192.168.0.3 and 
FTP Server : 192.168.0.5


Thanks :)

---

### Post by Kyroswolf on 2009-09-01
I just finished configuring my own ftp server.

My router allows for port forwarding.  In the firmware of the router it is called a Virtual Server.  I simply setup a rule for inbound TCP traffic on Port 21 to forward to port 21 on the private IP of my server.  If you would like I can post more when I'm home and have access to the UI of my router.

---

### Post by Abu Hauna on 2009-09-01
Yes, I would. Thanks Kyroswolf

---

### Post by Kyroswolf on 2009-09-01
I just re-read your OP.  Are you using a router as your gateway or a computer set up as a gateway.  If it is a router what brand/model.  If it is a computer what OS is it running?

---

### Post by Abu Hauna on 2009-09-01
I'm just using computer set up as gateway. It's Ubuntu Linux Server 8.04 LTS.

---

### Post by Kyroswolf on 2009-09-01
Ok, then as I said it is going to be a port forwarding setting.  Since port 21 is reserved for FTP traffic you will need to forward port 21 to your ftp servers private IP address.  I'm not sure how Ubuntu handles port forwarding.  My own is Ubuntu Server 9.04 and it is setup as a file/ftp server.  I'd suggest checking the ubuntu documentation.  I'll dig around to in breaks here at work.  I love a good puzzle.

---

### Post by dmizer on 2009-09-01
> **Abu Hauna said:**
> I'm just using computer set up as gateway. It's Ubuntu Linux Server 8.04 LTS.

If you have a dedicated computer for this task, I highly suggest something like [Untangle](http://www.untangle.com/home), [Clarkconnect](http://www.clarkconnect.com/), or [some other dedicated gateway OS](http://en.wikipedia.org/wiki/List_of_router_or_firewall_distributions). This would provide you with a much more secure arrangement, a nice fancy web interface for configuring it, and you wouldn't have to mess with IPtables.

A huge advantage to these dedicated gateway operating systems is that they have a huge range of plugins which allow you to easily enable gateway services like FTP, VPN, as well as more complicated tasks like email and web hosting.

Now I understand that you may want to learn how to work IPtables, and that this may be an experiment. That's fine, but do your IPtables experimenting on a subnet without WAN access. That way, when you make a critical mistake (and you will make one) while learning how to configure IPtables, you don't end up putting your entire network at risk. It's one thing to want to expand your knowledge, it's an entirely different matter to compromise your network during that learning experience.

All I'm suggesting here is that you use the right tool for the job, but network security is nothing to trifle with these days.

---

### Post by Kyroswolf on 2009-09-01
I found this.

[http://www.howtoforge.com/nat-gateway-iptables-port-forwarding-dns-and-dhcp-setup-ubuntu-8.10-server](http://www.howtoforge.com/nat-gateway-iptables-port-forwarding-dns-and-dhcp-setup-ubuntu-8.10-server)

The bottom of this tutorial shows how to setup IP Tables.  These can be used to start port fowarding.

So....

sudo vi /etc/sysctl.conf

Uncomment:  net.ipv4.ip_forward=1

Save

sudo vi /etc/rc.local

Add this to bottom of file

/sbin/iptables -P FORWARD ACCEPT
/sbin/iptables --table nat -A POSTROUTING -o eth0 -j MASQUERADE

Save

Now sudo vi /etc/rc.local

Add this to bottom of file
/sbin/iptables -t nat -A PREROUTING -p tcp -i eth0 -d <hostname> --dport 21 -j DNAT --to 192.168.0.5:21
Replace <hostname> with your own hostname.

Let me know if that works.

---

### Post by Abu Hauna on 2009-09-02
@dmizer
Thanks for your advice. I had tried untangle. It's simple gateway. But I'm still not experience more distant yet.

@Kyroswolf
Still not working yet.

---

### Post by Kyroswolf on 2009-09-02
Have you tried Smoothwall?  This is a great firewall/gateway OS.  Sorry what I found last didn't help.

---

### Post by Abu Hauna on 2009-09-02
No, I haven't. 
Ok, I will try it. No worry, thanks a lot...

---

### Post by dmizer on 2009-09-02
> **Abu Hauna said:**
> @dmizer
Thanks for your advice. I had tried untangle. It's simple gateway. But I'm still not experience more distant yet.

Untangle has lots of well written howtos with step-by-step instructions here: [http://wiki.untangle.com/index.php/Main_Page](http://wiki.untangle.com/index.php/Main_Page)

If you're having trouble with Untangle, then you should seriously consider just using a hardware router until you can get enough networking understanding to make your own Linux firewall. And most certainly, you should avoid trying to hand configure IPtables.

---

