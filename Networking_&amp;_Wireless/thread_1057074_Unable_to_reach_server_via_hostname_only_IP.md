---
title: "Unable to reach server via hostname only IP"
date: 2009-02-01
forum: Networking &amp; Wireless
---

### Post by meighty on 2009-02-01
Here is the setup. 

PfSense as the firewall/router. 
1 Desktop running Vista 
2 Laptops (wireless) running vista and XP 
1 Ubuntu 8.10 Server. 

I'm using DHCP on my server with mac assigned IPs from the router. 
I have Samba installed and working.
I'm unable to ping via hostname from server to windows machine. 

I'm able to ping my server when I use an IP. This however, wasn't always the case. About a week ago I was running off a DD WRT linksys router and everything was going great. One day, out of the blue I wasn't able to reach my server via hostname. 

I checked my basic settings. Everything seemed right. 

I checked my winbind settings. All great.

Checked my dhclient.conf for send hostname. All fine.

Tried adding .local to the end of the hostname and no luck.

When I try and ping from windows I get this.

C:\ping storage01
Ping request could not find host storage01. Please check the name and try again.


Thoughts?

---

### Post by meighty on 2009-02-01
Testing from my ubuntu laptop I'm still not able to see the server via hostname.

---

### Post by AlanR8 on 2009-02-01
Have you tried this? Unknown source from these forums. Respect, worked for me!

> edit /etc/nsswitch.conf

Rem (#) the line that says
Quote:
hosts: xxxxxxxxxxxxxxx

to this:
Quote:
hosts: files dns wins 

finally, you need to install winbind
Code:
sudo apt-get install winbind
that's all that it took for me.


---

### Post by meighty on 2009-02-01
Here is my nsswitch.conf 

> 
# /etc/nsswitch.conf

hosts:          files mdns4_minimal [NOTFOUND=return] dns wins mdns4
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis



I'll give yours a shot. I already have winbind installed. Hopefully this works. 

Thanks for the reply!

---

### Post by meighty on 2009-02-01
Bummer. No luck. I'm gettin no love from my server today...  :(

---

### Post by AlanR8 on 2009-02-01
You did reboot....

---

### Post by meighty on 2009-02-01
First I restarted my networking and that didn't work...

So I tried doing a full reboot and still no luck.

---

### Post by andrew.mckevitt on 2009-02-01
> **AlanR8 said:**
> Have you tried this? Unknown source from these forums. Respect, worked for me!

Quote:
edit /etc/nsswitch.conf

Rem (#) the line that says
Quote:
hosts: xxxxxxxxxxxxxxx

to this:
Quote:
hosts: files dns wins

finally, you need to install winbind
Code:
sudo apt-get install winbind
that's all that it took for me. 

This did not work for me either, although i could now connect 'smb://home-server', it was still no use as 'network:///' produced nothing, and as a bonus, I lost remote desktop connection too. Be warned. mdns4(blah blah) is there for a reason.

---

