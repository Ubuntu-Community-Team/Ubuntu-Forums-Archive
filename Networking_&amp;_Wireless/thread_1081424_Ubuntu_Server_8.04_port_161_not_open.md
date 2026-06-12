---
title: "Ubuntu Server 8.04 port 161 not open?"
date: 2009-02-26
forum: Networking &amp; Wireless
---

### Post by wililupy on 2009-02-26
Hello.

I have an Ubuntu Server 8.04 box that is a LAMP server. We use Intermapper to monitor our network. 
I install snmpd on the server from the repository and have it setup so that if I run snmpwalk -v1 -c public localhost I get information about the server, however, when I try to connect to it from intermapper, it fails, and if I run snmpwalk -v1 -c public hostname it fails to connect even from the console.
I ran a port sniffer against the server and port 161 doesn't show open. I beleive this is the error. 
Unfortunatly, I have no idea how to open this port. I don't have any firewall installed on the server. It is just a standard LAMP server with snmp and that is it. I can browse the web pages and run SQL queries against it no problem, so I know that is configured properly.
Any ideas?

Thanks.

---

### Post by jonobr on 2009-02-26
HEllo


Couple of questions/thoughts

Im guessing you can ping hostname when you do your snmpwalk query and that using IP address does the same thing?

You also mention using a port sniffer,
are you using wireshark/tcpdump?

If by saying port 161 doesnt show up, you mean you dont see the SNMP query 
in the trace you do, then that means the packet is not getting to the server.

Whether the daemon is running or not, or whether the SNMP packet is actually proccessed by the server, is a secondary issue, the fact that your tcpdump/wireshark doesnt see the packet means it probably never reached the server.

If it was received by the server, and the problem was related to an unopen port, Im pretty sure you would see that in a trace from the querying machine.
You would see the packet go out, but the response would say something like application not available.

My recommendation is you look at the querying end and run a wireshark/tcpdump to ensure the packet is beign issued and if there is a response of some kind from the server.

Also, wondering why your not using V2 or V3?
V2 allows for more flexibilty with queries such as getbulk getnext, whereas V3 allows additional security.

---

### Post by wililupy on 2009-02-26
Actually, I figured it out.

I ran ps -ef |grep snmpd 

It output the following:

snmp 25017 1 0 12:49 ? 00:00:00 /usr/sbin/snmpd -Lsd -Lf /dev/null -u -snmp -I -smux -p /var/run/snmpd.pid 127.0.0.1.

I thought it odd that it only be listening on lo, so I ran /etc/init.d/snmpd stop and then manaully ran the snmpd with the above command minus the 127.0.0.1.

I then ran snmpwalk -v1 -c public hostname and walla! it worked.

I then looked at the init.d script to see where it was getting this bogus startup script and found the culprit in /etc/default/snmpd.

In the /etc/default/snmpd file there is a line that says:


SNMPDOPTS='-Lsd -Lf /dev/null -u snmp -I -smux -p /var/run/snmpd.pid 127.0.0.1'

If you take out the 127.0.0.1 it works. 

What it ended up being was the init.d scripts was running this line to start the service and locking it down so that it was only listening to localhost on port 161 and not allowing any outside connections to the port. The way I found this out was by stopping the snmpd daemon and manually running it without the 127.0.0.1 at  the end and I was able to connect to it from intermapper and by hostname. I then edited the /etc/default/snmpd file and removed it so that it doesn't add it any longer.

Would have been nice to know that when they updated the package, that locked it out so that no outside connections would connect to it, and have a way to work around it so I wasn't scratching my head with this for 5 months.

---

### Post by jonobr on 2009-02-26
5 months, ..... heck, thats not fun...........

Congrats though, and would recommend you mark as resolved whiclst changing the title saying changes after update on snmp so that is makes it searchable to others who have the same trouble

---

