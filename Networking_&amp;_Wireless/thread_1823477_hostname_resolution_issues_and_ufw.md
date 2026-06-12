---
title: "hostname resolution issues and ufw"
date: 2011-08-12
forum: Networking &amp; Wireless
---

### Post by vincam24 on 2011-08-12
I just installed ubuntu server 11.04 and I am having issues detecting my machine on my LAN when ufw (uncomplicated firewall) is active. When ufw is disabled I can ping the hostname and ip address just fine, but once I enable ufw I can only ping the ip address and when I try to ping the hostname, it can't find the machine. As soon as i disable ufw i can ping the hostname fine again. i would suspect that it might be a dns issue except i don't have any problems pinging the hostname once ufw is disabled. 
 
i'm very new to ubuntu and i suspect that there is some setting that is put in place when i enable ufw that prevents my router (NETGEAR WNDR3400) from resolving my servers hostname to its ip address. I don't know enough about dns and hostname resolution to know what is going on.
 
I appreciate your help. Thanks.

---

### Post by vzDUCH on 2011-11-30
Nobody knows how to fix it?
I'm having same problem.

When UFW is enabled I'm able to ping IP but ping HOSTNAME returns "ping: unknown host HOSTNAME"

When UFW is disabled all is OK. Ping IP and ping HOSTNAME runs OK.

Looks like UFW is blocking it but could not find how to fix it.

---

### Post by Morbius1 on 2011-11-30
There's a BooBoo in the default settings of ufw concerning Samba that needs to be fixed. Give this a shot:

Edit: /etc/default/ufw

Change this:
> # extra connection tracking modules to load
IPT_MODULES="nf_conntrack_ftp nf_nat_ftp nf_conntrack_irc nf_nat_irc"To this:
> # extra connection tracking modules to load
IPT_MODULES="nf_conntrack_ftp nf_nat_ftp nf_conntrack_irc nf_nat_irc **[COLOR=#0000ff]nf_conntrack_netbios_ns[/COLOR]**"I'll put it in a code wrapper since it's really picayune about spaces:
```
IPT_MODULES="nf_conntrack_ftp nf_nat_ftp nf_conntrack_irc nf_nat_irc nf_conntrack_netbios_ns"
```Then disable and re-enable the firewall.
[COLOR=Blue]
EDIT[/COLOR]: Um ... you may have to restart the ufw service:
```
sudo service ufw restart
```

---

### Post by vzDUCH on 2011-11-30
> **Morbius1 said:**
> There's a BooBoo in the default settings of ufw concerning Samba that needs to be fixed. Give this a shot:

Edit: /etc/default/ufw

Change this:
To this:
I'll put it in a code wrapper since it's really picayune about spaces:
```
IPT_MODULES="nf_conntrack_ftp nf_nat_ftp nf_conntrack_irc nf_nat_irc nf_conntrack_netbios_ns"
```Then disable and re-enable the firewall.
[COLOR=Blue]
EDIT[/COLOR]: Um ... you may have to restart the ufw service:
```
sudo service ufw restart
```


That solved my problem.
Thanks a lot.

---

