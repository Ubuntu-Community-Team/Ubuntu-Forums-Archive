---
title: "Configuration problem whit DHCP3"
date: 2009-03-10
forum: Networking &amp; Wireless
---

### Post by cayaman on 2009-03-10
Hello everyone

I'm trying to setup a DHCP3 server whitout succes

1- I have configured dhcpd.conf whit these parameters:

[B]
option domain-name-servers 10.0.0.1;

default-lease-time 60;
max-lease-time 72;

ddns-update-style none;

authoritative;

log-facility local7;

subnet 10.0.0.0 netmask 255.255.255.0 {
  range 10.0.0.100 10.0.0.254;
  option routers 10.0.0.1;
  option domain-name-servers 10.0.0.1;
}[/B]


2- I want to launch dhcp3 on mon0 interface, so here is my command line:

**ifconfig mon0 up 10.0.0.1 netmask 255.255.255.0**



3- JSo I fire up DHCP3:
[B]
dhcpd3 -cf /etc/dhcp3/dhcpd.conf mon0[/B]


4- Then I received the following results:

[B]
cayaman@cayaman-laptop:~$ sudo dhcpd3 -cf /etc/dhcp3/dhcpd.conf mon0
[sudo] password for cayaman:
Internet Systems Consortium DHCP Server V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Wrote 0 leases to leases file.
mon0: unknown hardware address type 803
Listening on LPF/mon0//10.0.0/24
Sending on   LPF/mon0//10.0.0/24
Sending on   Socket/fallback/fallback-net
Can't create PID file /var/run/dhcpd.pid: Permission denied.[/B]




Can you help me ??? How come it  **Can't create PID file /var/run/dhcpd.pid: Permission denied** ?



Do not hesite to ask me more infos.  Thanks in advance !

---

### Post by skeiths on 2009-06-02
Does anyone know how to fix this error?

I have read that 
restorecon -v /var/run /var/run/dhcpd.pid
might fix it but I dont know what the above does and i need to install policycoreutils

will the above command fix this error and is it the correct thing to do?

---

### Post by noneroy on 2009-08-05
I'm having the exact (and I mean exact since I'm looking at the Karma documentation too ;) problem with Ubuntu 9. I noticed there are some bug reports about this but I've not read any solutions.

Also the solution you found by googling does not fix the issue. For some reason it cannot create this PID file. Any suggestions would be very appreciated.
```

```

---

### Post by GuiltySpark on 2009-08-18
***[FONT=Palatino Linotype][SIZE=4]Bump...I got this problem as well someone please help?[/SIZE][/FONT]***

---

### Post by skeiths on 2009-08-19
> **GuiltySpark said:**
> ***[FONT=Palatino Linotype][SIZE=4]Bump...I got this problem as well someone please help?[/SIZE][/FONT]***

Try starting dhcpd3 with this script.

/etc/init.d/dhcp3-server start


Its pid will be at /var/run/dhcp3-server/dhcpd.pid

---

### Post by sm_arty on 2010-07-29
Solved for me
ln -s /var/run/dhcp3-server/dhcpd.pid /var/run/dhcpd.pid
dhcpd3 -cf /etc/dhcp3/dhcpd.conf at0

---

### Post by postry on 2011-07-26
I did something like this:
downlaoded dhcp server source files from: [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

than unpuck it, and in main directory: 

$ cd server
$ make clean all

executable file show up: dhcpd

$ sudo ./dhcpd -cf $PWD/dhcpd.conf -lf $PWD/dhcpd.leases.5 -pf $PWD/killme.pid eth1
or 
$ sudo ./dhcpd -cf /etc/dhcp/dhcpd.conf eth1 -pf killme.pid -lf dhcpd.leases.5

And I got this:
Internet Systems Consortium DHCP Server 4.2.1-P1
Copyright 2004-2011 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)
Wrote 0 leases to leases file.
Listening on LPF/eth1/00:1d:60:1c:a9:70/192.168.2.0/24
Sending on   LPF/eth1/00:1d:60:1c:a9:70/192.168.2.0/24
Sending on   Socket/fallback/fallback-net
davinci@postry-System-Product-Name:~/Downloads/dhcp-4.2.1-P1/server$ 

It looks like it is working, I also got IP on this interface.

---

### Post by brainbuz on 2011-10-30
There are two ubuntu packages of dhcpd -- dhcp3-server and isc-dhcp-server. The former package is an obsolete version, you should be installing the latter package. 
When I realized this I uninstalled both packages (and it seems I had managed to have them both installed). Then I installed  isc-dhcp-server. The command: 'service isc-dhcp-server' can start and stop the service, and it is servicing clients.

---

### Post by Guardian Angel on 2013-04-11
> **sm_arty said:**
> Solved for me
ln -s /var/run/dhcp3-server/dhcpd.pid /var/run/dhcpd.pid
dhcpd3 -cf /etc/dhcp3/dhcpd.conf at0

Solved for me too.
Thanks!

---

### Post by Iowan on 2013-04-11
Old thread.

---

