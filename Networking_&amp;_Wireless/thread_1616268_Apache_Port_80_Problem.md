---
title: "Apache Port 80 Problem"
date: 2010-11-08
forum: Networking &amp; Wireless
---

### Post by edge2022 on 2010-11-08
I am running Ubuntu 10.04, and I have been trying to get my Apache server running.  I am running TWiki on Apache, and all functions work fine using localhost and my computer's internal IP (192.168.1.109).  When I try to load the site using my external IP (97.93.51.230) I get a time out error.  Also, when I use this: [http://www.yougetsignal.com/tools/open-ports/](http://www.yougetsignal.com/tools/open-ports/) to check whether port 80 is open, it also tells me that the port is closed and gives a time out error.  I am sure Apache isn't the problem since running lsof -i tells me that Apache is listening on port 80.  I also set up my router to forward port 80 to my internal IP.  Is there a firewall I have to set up, or is it my ISP that is blocking port 80?

By the way, I also tried to make Apache listen to port 3000, and using localhost:3000 worked fine.  But, using the open port tool, I still got a time out error.  Lsof -i also tells that apache is listening on port 3000.

Thank you for reading.

---

### Post by lisati on 2010-11-08
You might need to set your router to forward port 80 (or whatever) to your server. Feel free to let us know if this doesn't help or you get stuck.

---

### Post by Barriehie on 2010-11-08
Highly likely your ISP is blocking the port.

---

### Post by edge2022 on 2010-11-08
I have attached a screen shot of my router's port forwarding configuration.  Would my ISP also block port 3000 as well as 80?

---

### Post by zexelon on 2010-11-08
For the record, I have been having a terrible time getting my Linksys WRT310Nv2 to properly port forward, I actually had to remove it from being the router as I could not get it to port forward anything properly. 

Have you tried directly connecting your box to the internet?

If I had to blame something I would peg the Linksys.

---

### Post by edge2022 on 2010-11-08
O, I have a Linksys WRT54GR.  I can't practically connect my computer directly to my modem since my desktop is upstairs, and my modem is down.  But, if I can isolate the router as being the problem, I will try it with a laptop.

---

### Post by holiday on 2010-11-08
Sometimes trying your external IP from your LAN will fail if your router does not support loopback forwarding. I had to replace a DLink that didn't support it. 

The port scan result makes me think probably something else is up, but check that your router does support loopback forwarding.

---

### Post by edge2022 on 2010-11-08
I tried to turn on Filter NAT Internet Redirection in the Security tab of my router, but I still cannot access it from my external IP.  I'll try forwarding a range of ports.  I'm not sure if my router supports loopback forwarding... i'll check.

---

### Post by Barriehie on 2010-11-08
These links might help determining what ports are open/blocked.

[Open Port Check Tool](http://www.canyouseeme.org/)

[Shields Up](https://www.grc.com/x/ne.dll?bh0bkyd2)

---

### Post by uncaspi on 2010-11-08
I think it`s the firewall in your server. List rules in iptables with this sudo iptables -L

Open port 80 with this

iptables -A INPUT -p tcp --dport 80 -j ACCEPT

Restart the iptables service

---

### Post by edge2022 on 2010-11-08
uncaspi, I entered the command to open port 80, and it went though.  Now, iptables lists it as a rule.  But, I'm not sure of how to restart iptables since service iptables stop gives an error of unrecognized service.

btw, after talking with Linksys tech support, loopback forwarding is not supported on my router.  But after having a friend failing to connect with a time out error, I still need to figure out how to open up port 80 or 3000.
i've also tried disabling the firewall on my router, and put it in a DMZ.  That didn't help.

Also, I have ufw enabled and a rule created to allow port 80 incoming traffic.

---

### Post by uncaspi on 2010-11-08
First you must save the rule you applied.

sudo iptables-save

I googled for start stop iptables and some use firestarter with CLI. I think the easiest way is to reboot.

No need for disabling firewall in the router. Just do what you did. Allow traffic  to http port and give the ip to your server in the firewall.

Dont think it has to do with loopback forwarding in your router.

---

### Post by edge2022 on 2010-11-12
I read around and found out that you would have to save the iptables rule to a file, and restore it at each startup.  Of course you can do it with a script, but adding the rule has not change anything.  I changed by computer's IP to 192.168.1.150 so that it is out of the DHCP range of the router.  But that didn't help either.

My modem is a Motorola SB5101U, and it looks like a regular modem rather than a model/router combo.  So it cannot be the problem.  I read that in the router's configuration, the Internet IP Address should be the external IP of the modem, but instead it is 192.168.15.2  Could that be the issue?

---

