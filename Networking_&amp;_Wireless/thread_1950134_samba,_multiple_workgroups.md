---
title: "samba, multiple workgroups"
date: 2012-03-31
forum: Networking &amp; Wireless
---

### Post by pratikk on 2012-03-31
My 10.10 laptop travels to at least three Win workgroups every day. Every change of location, I change the workgroup name in /etc/samba/smb.conf and all is good. But is there a better way, like having all the workgroups the machine visits registered somehow? 

TIA

Pratik

---

### Post by nothingspecial on 2012-04-01
*Thread moved to **Networking & Wireless**.*

---

### Post by headvampyre@hotmail.co.uk on 2012-04-01
In order to do this you could (possibly) run a samba virtual server for each network.
Basically, this consists of adding:
smb ports = 139
netbios aliases = wgserver1 wgserver2 wgserver3
include = /etc/smb/smb.conf.%L

into /etc/smb.conf, and then creating a config file for each virtual server.

Name the three configurations:
smb.conf.wgserver1
smb.conf.wgserver2
smb.conf.wgserver3

And then make sure the original smb.conf (the only one with the smb ports, aliases and includes in) only contains those three lines and the netbios names. Put a seperate workgroup name within each virtual server configuration.

---

### Post by Morbius1 on 2012-04-01
May I ask why you feel it's necessary to have your workgroup match everyone else's?

---

### Post by pratikk on 2012-04-02
Thanks a lot! I think I understand the logic, and I'll try it out  soonest. My smb.conf is in /etc/samba, not /etc, so I suppose that's  where I should put the smb.conf.win files. 

Thanks

Pratik

---

### Post by pratikk on 2012-04-02
Morbius, it's to use files on Win machines in these workgroups. As far as I know, the workgroup names have to match on each network?

---

### Post by Morbius1 on 2012-04-02
> **pratikk said:**
> Morbius, it's to use files on Win machines in these workgroups. As far as I know, the workgroup names have to match on each network?
[COLOR=Blue]*Note: I logged into a Win7 machine before I made this post just to make sure something hasn't changed.*[/COLOR]

I see posts like yours from time to time. I have even seen HowTo's - both Linux and Windows - that insist that they must be the same. I have several workgroups in my LAN and I have no problem discovering or accessing shares in either direction across workgroups.

It does make discovery a whole lot easier from a Linux client perspective if the workgroups do match only because Linux lists all the workgroups requiring me to wade through each one of them before I find the Win7 host. 

From the Win7 client's perspective the user is presented with a list of hosts and there is no reference at all to the workgroup. The WIn7 client user doesn't even know there are 2 workgroups.

Now, my network is simple in that all machines are connected ( wired or wirelessly ) to the same router so everyone's in the same subnet. Perhaps the networks you find yourself in are more complex.

---

### Post by pratikk on 2012-04-02
Morbius, that's a very interesting tip which I'm going to explore. In my case, the workgroups are on different LANs. if this behaviour works across them, it would simplify life enormously. I'll try it as soon as the spring break is over.

---

