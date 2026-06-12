---
title: "DNS settings."
date: 2005-12-15
forum: Networking &amp; Wireless
---

### Post by spacifique1 on 2005-12-15
I am using a pppoa dsl connection and i had to change the DNS settings to be able to use firefox. The problem is that each time i shut down my pc and restart, i have to redo the DNS settings. Any help on how to make these settings permanent?
Thanks.

---

### Post by darth_vector on 2005-12-15
edit the file /etc/resolve.conf as root. add one line of the sort:

nameserver <ip_of_dns_server>

for each dns server you wish to use. the top one will be the primary dns, the second the secondary, and so on...

---

### Post by runlevel0 on 2005-12-15
[QUOTE=spacifique1]I am using a pppoa dsl connection and i had to change the DNS settings to be able to use firefox. The problem is that each time i shut down my pc and restart, i have to redo the DNS settings. Any help on how to make these settings permanent?
Thanks.[/QUOTE]

DHCP?

DHCP rewrites the DNS entries each time it restarts. This can be prevented changing the permissions of /etc/resolv.conf, but I'm not sure that DHCP will not complain.

Setting up a static IP would avoid this and other problems. It's as easy as 1-2-3, just *sudo kate /etc/network/interfaces*
and write this:
```


auto eth0        # automatic start at boot

iface eth0 static                #in case of a USB  modem it's nas0
  address 192.168.x.y
  netmask 255.255.255.0
  gateway 192.168.x.y

```

Restart the network * sudo /etc/init.d/network restart*

To test if it works: * ping -c 1 [www.google.com](www.google.com)*.

Hope it helps.

---

### Post by Lambert on 2005-12-15
I have not used this but here something you can try. Post back if it works.

Edit this file using sudo or root privledges.

 /etc/dhcp3/dhclient.conf 

Add these lines to it.


supersede domain-name "nameserverdomain.here.com"; 
prepend domain-name-servers "x.x.x.x"

no quotes or puncutuation in statments. replace x.x.x.x with the ip address of the name server.

---

### Post by mlomker on 2005-12-15
[QUOTE=Lambert]
supersede domain-name "nameserverdomain.here.com"; 
prepend domain-name-servers "x.x.x.x"
[/QUOTE]

At the risk of presenting too many options, my preferred solution is to install the **resolvconf** package.  It allows you to set interface priorities so that whenever your Internet connection is up its DNS settings will be preferred and it'll go away when the link comes down.  I use it to manage my VPN connections to work and it's slick.

Lambert's solution would work but changes to dhclient configs affect all addresses obtained by DHCP.  That isn't a problem on a desktop PC but if you have a laptop then that isn't a good approach.

---

