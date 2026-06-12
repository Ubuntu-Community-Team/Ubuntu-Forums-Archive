---
title: "No DHCPOFFERS received."
date: 2010-01-03
forum: Networking &amp; Wireless
---

### Post by Biddlesby on 2010-01-03
I've managed to (I think) get my network card talking, but stuck at the DHCP.

Network is wired, /interfaces looks like this:

> auto eth0
iface eth0 inet dhcpBut on networking restart I get

>  * Reconfiguring network interfaces...                                          
There is already a pid file /var/run/dhclient.eth0.pid with pid 1690
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.2
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:10:dc:c9:ac:d3
Sending on   LPF/eth0/00:10:dc:c9:ac:d3
Sending on   Socket/fallback
grep: /etc/resolv.conf: No such file or directory
Internet Systems Consortium DHCP Client V3.1.2
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:10:dc:c9:ac:d3
Sending on   LPF/eth0/00:10:dc:c9:ac:d3
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
grep: /etc/resolv.conf: No such file or directoryPlenty of leases available, according to the router. All the other windows and mac pcs on the network get their ip's fine. Any ideas?

---

### Post by Iowan on 2010-01-03
[This]("http://ubuntuforums.org/showthread.php?t=1156441") solved my DHCP problem on Jaunty - curiously, my Karmic box doesn't seem to have the same issue. There was a Launchpad question that solved the problem:> 
Bee said on 2009-12-25:

Well thanks to everyone, but problem was actually solved by editing dhconfig.conf file: i added a string

send vendor-class-indentifier "MSFT 5.0";

That solved the problem, and now my linux is masking under windows when log in.


---

### Post by Biddlesby on 2010-01-04
Thanks iowan, I'll give it a go.

---

### Post by Biddlesby on 2010-01-04
It works! :)

---

### Post by Iowan on 2010-01-04
:shock:
Which one?
(Or did you shotgun it and change both? Leave it if it's working.)

---

### Post by Biddlesby on 2010-01-05
Well, I commented out the `'option rfc3442'' line and removed the relevant bit in the ``request'' line and it still didn't work, so I added the ``send vendor-class-indentifier "MSFT 5.0";'' line and it did. But I don't know if its the combination of the two!

---

### Post by naradluffy on 2011-09-08
I am sorry, but where is dhconfig.conf. what should i write???

---

