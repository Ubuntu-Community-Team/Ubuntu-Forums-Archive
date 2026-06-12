---
title: "Run script after a specific kernel message"
date: 2011-10-05
forum: Networking &amp; Wireless
---

### Post by Seb_Boffen on 2011-10-05
My setup an ubuntu 10.04 server acting as internet gateway, (including Dhcp, Dns, Webserver, Ftp, Email etc. all in one server) Eth0 is the link to internet, eth1 is the link to the local network.
 
When the link of eth0 goes down and up I'd like to run a script [COLOR=black][FONT=Verdana]automatically[/FONT][/COLOR] to restore ip forwarding:
 
iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
echo 1 > /proc/sys/net/ipv4/ip_forward
iptables-save | tee /etc/iptables.sav
 
my message log looks like: 
 
Oct 5 21:00:46 xxx kernel: [64411.446886] r8169: eth0: link down
Oct 5 21:00:48 xxx kernel: [64413.579442] r8169: eth0: link up
Oct 5 21:01:04 xxx kernel: [64429.628960] r8169: eth0: link down
Oct 5 21:01:06 xxx kernel: [64431.789312] r8169: eth0: link up
 
This then should help my local network to have internet access restored [COLOR=black][FONT=Verdana]immediately[/FONT][/COLOR] after such an event, I noticed that the restore does not always take place from /etc/iptables.sav
 
Any help would be welcome.

---

### Post by Toz on 2011-10-05
Hello and welcome to the forums.

I believe you can add an executable script to the /etc/network/if-up.d directory for it to be executed everytime and interface goes up.

**/etc/network/if-up.d/restore_ip_forwarding**
```
#!/bin/bash
/sbin/iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
/bin/echo 1 > /proc/sys/net/ipv4/ip_forward
/sbin/iptables-save | /usr/bin/tee /etc/iptables.sav
```

---

### Post by Seb_Boffen on 2011-10-05
Thank you very much, this will work.

---

