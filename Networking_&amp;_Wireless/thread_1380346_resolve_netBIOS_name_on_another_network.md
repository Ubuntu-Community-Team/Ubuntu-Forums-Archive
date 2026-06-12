---
title: "resolve netBIOS name on another network"
date: 2010-01-13
forum: Networking &amp; Wireless
---

### Post by thgis on 2010-01-13
Hi.

I'm new to linux and this forum so bare with me.
I want to setup a ubuntu file server with samba. I have samba working but only on my own network.

I want to place my ubuntu machine before my router which means that it is not local with respect to my laptop and desktop that is behind my router (others must also be able to access it). The ubuntu machine doesn't have a display,mouse and keyboard so I control it through ssh. My problem is that I dont know the ip the server gets when it is connected before my router (it gets it from a DHCP server) I only know the NetBIOS name that I have given it i the samba.conf file.

Can somebody tell me how I can get the servers ip? must I set up some other service for this purpose?

Regards, Thomas

---

### Post by Iowan on 2010-01-13
Hope you've got a good firewall running... 
[Here]("http://ubuntuforums.org/showpost.php?p=8599983&postcount=3") are links to a couple of DNS hosting places.

---

### Post by thgis on 2010-01-14
It is not on the global net. My router and my linux machine is connected to the network of my dorm.
My firewall is set to only allow ssh and samba. Samba is running with security=user in the samba conf file.
My problem is simply that I dont know which ip address my server is going to get when I connect to the dorm network. How to I find it when I only know the NetBIOS name? do I need to have some special service running on my linux machine?

Hope somebody can help me.

Thomas

---

### Post by Iowan on 2010-01-14
Hmmm... that makes it a li'l trickier. Depending on what the DHCP/DNS server is running, you *might* be able to use the "send host-name" line in */etc/dhcp3/dhclinet.conf* to associate the hostname with an IP address.

---

### Post by thgis on 2010-01-15
Thanks for your reply.
It seems that I already have a line like that.
snip of dhclient.conf that is not commented out

```
option rfc3442-classless-static-routes code 121 = array of unsigned integer 8;
send host-name "<hostname>";
...
request subnet-mask, broadcast-address, time-offset, routers,
    domain-name, domain-name-servers, domain-search, host-name,
    netbios-name-servers, netbios-scope, interface-mtu,
    rfc3442-classless-static-routes, ntp-servers;
```

Lets say that it actually sendt its hostname.. should I be able to use that hostname when I'm behind a router and the linux machine is not?

regards,
Thomas

---

### Post by efflandt on 2010-01-15
Typically to access netbios, Win file/printer sharing, or samba from a different LAN or network, both machines need to access a specific "wins" server (samba can do wins if properly configured).  That may be difficult if your router is not running Linux and/or it has a dynamic IP that changes.  We do not know if dhcp for your dorm is even going to pay attention to a netbios name you attempt to specify for the dorm DNS.  And you would need to have the proper ports forwarded through your local NAT or masquerade to the server.

I suppose you could use a dynamic dns service, but you would need to tell the service the specific dorm LAN IP of your router, because just tickling a dynamic dns service would grab the pubilc IP of the network you are on.

Just as an example, but not for that purpose, I have a Linux box behind my DSL wireless/modem/router and run a Perl script as a daemon that parses the web page of my modem and only notifies no-ip.com of my DSL IP address when it changes (to minimize internet traffic for it).  So I can always find my home system from the internet by its no-ip.com names (several names to experiment with virtual name based web server).

---

### Post by thgis on 2010-01-15
Hmm... okay.
I know that if I connect my computer directly to the dorm network I can connect to it by using its hostname from another computer that is directly on the dorm network too.

Just to be perfectly sure that my network layout is understood I have tried to draw it underneath


DORM NETWORK (With a DHCP server)
________________________________
| ............                                                |...................                                                   |
                                                    ...............|....................
                          ...............|_______......
                                                    ...............|.............|......
                        .............[R]...........[L]...
                                                    ...............|....................
                 ......_____|....................
                                   ......|.......               |...................
...[LAP] [DESK].............

(The dots should be regarded as white spaces...)

Where [R] is my router, [L] is my linux server, [LAP] is my laptop and [DESK] is my desktop. I want other people on the dorm network to be able to connect to the linux machine (Including my self)

Right now I have tried a solution where I specify a static ip to my linux server. This seems to work but also means that I cant get the linux server on the net and still cant use its NetBIOS name.. But I know which ip its having.

Any other suggestions?

Regards, Thomas

---

