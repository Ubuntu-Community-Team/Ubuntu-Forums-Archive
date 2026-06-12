---
title: "Ubuntu Server UFW IP masquerade / routing troubleshooting"
date: 2010-02-26
forum: Networking &amp; Wireless
---

### Post by MikeHHNeedsHelp on 2010-02-26
Hello and thanks for your time;

I'm trying to set up a box with Ubuntu 9.10 (server edition) to use as a small network server and router. I've been trying to follow the Ubuntu Documentation on ufw ([https://help.ubuntu.com/8.04/serverguide/C/firewall.html)]("https://help.ubuntu.com/8.04/serverguide/C/firewall.html") to get internet accsess to my private network, but I'm haveing problems - in particular, when I attempt to re-enable ufw, I get an error:
> ERROR: problem running ufw-initI really have no idea what is causeing the problem, so I'm going to append everything I think might be related; sorry for the information overload.


[LIST]
[*]My network topology: [cable : modem : ethernet] <-> [ eth0 : Server : eth1 ] <-> [ port 1 : 8-port switch : port n] <->>> [ethernet : local network machines]
[*]I've installed DHCP3-server on the server box, and am correctly being assigned IP addresses on local network machines.
[LIST]
[*]DHCP passes the internal network NIC IP as the DNS, wich I want for local interactions, but fails to pass my ISP's DNS as a secondary DNS
[/LIST]
 
[*]I've installed bind9 as a DNS and attempted to config it, but it's not working - I understand that it isn't nessesary in order to configure internet accsess, but I mention for completness.
[*]All other forms of service, ssh, www, ftp, samba, etc... are being correctly served to the local network machines, though the typical server programs, SSH, Apache2, vsftpd, samba...
[*]the default ufw config file: (/etc/default/ufw) _**[ATTACH]148266[/ATTACH]**_
[LIST]
[*]Note that the "DEFAULT_FORWARD_POLICY" is set to ACCEPT
[/LIST]
 
[*]The UFW sysct1.conf file: (/etc/ufw/sysct1.conf) _**[ATTACH]148267[/ATTACH]**_
[LIST]
[*]Note that ip_forwarding is enabled for both ip_v4 and ip_v6.
[/LIST]
 
[*]The UFW before.rules file: (/etc/ufw/before.rules) _**[ATTACH]148265[/ATTACH]**_
[LIST]
[*]Note that I've added the : POSTROUTING NAT directive and the postrouteing rule, as well as the two ufw-before-forward rules at the end of the file. (there's no space in the file - : P comes up as :P in the forum entry without the space)
[*]Adding just the postrouteing NAT directive and rule, without the forwarding rules, results in the same error.
[/LIST]
 
[*]I can see the internet from the server box itself - pinging works, apt-get can see the ubuntu servers, and my current workaround for internet involves an SSH tunnel to a squid server on the server box. (the tunnel-to-squid solution isn't tennable as an end result - I need to be able to serve internet to my network without a proxy)
[*]As a side note, I've also tried useing just iptables to route traffic through the server, as per the ubuntu documentation above - when I do, I can't see my sever box services from my local network machines, and still no internet even with static IP's, but I CAN ping my ISP.
[/LIST]
I'm certain it's something simple - Please help!!!

---

### Post by MikeHHNeedsHelp on 2010-02-26
Update: 
 I've found that adding the COMMIT line after the : POSTROUTING rule in the /etc/ufw/before.rules file will allow UFW to be enabled, but still nothing works. I understand that it's ignoreing everything in the file after the COMMIT directive - I think that means that there are conflicting rules in the before.rules file?

---

### Post by MikeHHNeedsHelp on 2010-02-26
Another Update: Disabling UFW and including the iptable rules as indicated in the Ubuntu documentation lets me see the internet from my local network. So, UFW is then blocking internet service despite the added lines in before.rules. 

I'm going to need a firewall, so help would still be appreciated!

---

### Post by uuesley on 2010-12-13
may be a day late, a dollar short, and not applicable to you, however...

i started setting something similar to this today, and came across the same error message....my problem was fat fingers...i forgot a space between a T and a [, thus causing a context error....

YMMV....

w

---

