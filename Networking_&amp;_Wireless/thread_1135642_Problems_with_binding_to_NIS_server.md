---
title: "Problems with binding to NIS server"
date: 2009-04-24
forum: Networking &amp; Wireless
---

### Post by uli_kunkel on 2009-04-24
Hello, 

I have set up NIS on Server and Client as described in [https://help.ubuntu.com/community/SettingUpNISHowTo](https://help.ubuntu.com/community/SettingUpNISHowTo) and in /usr/share/doc/nis/nis.debian.howto.gz . I have checked the configurations files several times and I am convinced that they are ok. Yet, the client has a problem to bind ot the server and I don't know why. 

Restarting portmap and nis on the server works without problems : 
[FONT=monospace]$[/FONT] sudo /etc/init.d/portmap restart[FONT=monospace]
* Stopping portmap daemonn...                                   [ OK ]
* Starting portmap daemon...                                    [ OK ]
[/FONT]$ sudo /etc/init.d/nis restart
* Starting NIS services                                                                                [  OK  ]

But restarting nis on the client doesn't work : 
$ /etc/init.d/nis restart
* Starting NIS services       
* binding to YP server...    
*....                                                                                                                                                                                             *....                                                                                                                                                                        *....                                                                                                                                                                                             *....                                                                                                           [fail]
                                                                                                                [ OK ]
This is the entry in /var/log/syslog after the client unsuccessfully tried to connect to the NIS server : 
Apr 24 20:17:29 hodgkin dhclient: DHCPREQUEST of <null address> on eth0 to [ip of dhcp server] port 67
Apr 24 20:17:29 hodgkin dhclient: DHCPACK of [ip of nis client] from [ip of dhcp server]
Apr 24 20:17:29 hodgkin dhclient: bound to [ip of nis client] -- renewal in 228 seconds.

Hower the output of the command "ypbind -d" doesn't indicate any problems :
9161: parsing config file
9161: Trying entry: ypserver [ip of NIS server]
9161: parsed ypserver [ip of NIS server]
9161: add_server() domain: [NIS domain name], host: [ip of NIS server], slot: 0
9161: [Welcome to ypbind-mt, version 1.20.1]
9161: ping interval is 20 seconds
9162: ypbind-mt already running (pid 9001) - exiting

If I kill the ypbind-mt process (pid 9001 above) the command "ypbind -d" gives : 
9367: parsing config file
9367: Trying entry: ypserver [ip of NIS server]
9367: parsed ypserver [ip of NIS server]
9367: add_server() domain: GNT-CLUSTER, host: [ip of NIS server], slot: 0
9367: [Welcome to ypbind-mt, version 1.20.1]
9367: ping interval is 20 seconds
9369: NetworkManager is running.
9369: Are already online
9369: interface: org.freedesktop.DBus, object path: /org/freedesktop/DBus, method: NameAcquired
9370: ping host '[ip of NIS server]', domain '[NIS domain name]'
9370: host '[ip of NIS server]' doesn't answer.
...

I have switched of the firewall on the NIS server with "/etc/init.d/firestarter stop" the problem persists. 

Does anybody have an idea how I can find out whether the yp server is running correctly and if yes, why does the client cannot bind to it. It it not clear to me whether the problem is on the server or the client side. 

I have been trying to fix this problem for quite some time now and I am running out of idea. Any help is very appreciate. 

Cheers!
Uli

---

### Post by life-on-mars on 2009-07-07
The HOWTO doesn't say anything about editing /etc/defaultdomain on the client side. Once I edited the file, so it matched the server config, it worked like a charm.

on server AND client -> 
/etc/defaultdomain:
<yourNISdomain>

on server ->
/etc/yp.conf:
domain <yourNISdomain> server <yourNISserverIP>

on client ->
/etc/yp.conf:
ypserver <yourNISserverIP>

everything else is just like the HOWTO says.

---

### Post by 480silverton on 2009-10-09
There is only one thing wrong in the HOW TO

when it talks about the
/etc/defaults/nis

NISSERVER=master
NISCLIENT=false

That setting is wrong

Try doing this instead. Make the NISSERVER true instead of master
NISSERVER=true
NISCLIENT=false

---

