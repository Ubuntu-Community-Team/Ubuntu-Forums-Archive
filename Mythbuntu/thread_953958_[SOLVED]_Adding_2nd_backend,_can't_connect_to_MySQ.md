---
title: "[SOLVED] Adding 2nd backend, can't connect to MySQL but can ping.. help!"
date: 2008-10-20
forum: Mythbuntu
---

### Post by thalon on 2008-10-20
Hi all,
I'm ready to add a secondary backend to my setup.  I have opened up the MySQL permissions to accept connections from anywhere (I know, I know... just for testing), bound the primary backend database to the real IP instead of 127.0.0.1 (IIRC this is in place of removing --skip-networking according to the .conf file) and configured the real IP in both places in the primary's backend setup.  I can ping the primary from the new secondary, but when I go and configure the LiveCD environment and hit Test Connection it just reports back Failure without any further info.  I have tried with both the mythtv user and the root user which I know I have the correct credentials at least for the root user, so it is not a permissions problem.  I can ping the primary on the network, and can even telnet to its two MySQL ports and get communication.  Anyone have any ideas?  Thanks in advance for your help.

---

### Post by 4dognight on 2008-10-22
I have had this happen too when adding a slave backend. I cant recall the exact directories, but the mysql password info is stored in more than one place. One of those is prob configured wrong. Also, when your configuring your slave backend, use a static IP for the slave backend in the configuration, Not the 127.0.0.1. This hasnt anything to do with your current problem, but can cause problems for using the slave backend's tuners remotely.

---

### Post by thalon on 2008-10-22
I'm not so sure it's a permissions problem, because I can connect with the mysql command-line client on the local box itself as the user root, but I cannot connect from the secondary backend using the same credentials.  Or is it still possible that I need to configure mysql further?  Could someone please provide some more specifics?  I understand networking concepts but need some Linux/Mythbuntu-specific help.  Thanks!

---

### Post by uopjohnson on 2008-10-22
It sounds like you are having mysql authentication issues.  You can use the mysql command line remotly like this:
```
mysql -h BACKEND -u root -p
```
That will let you test if you are able to connect from a remote machine. Try it on your LiveCD and see what you get. 
If you get a failure then check yoru mysql permission by logging in to mysql on your backend like this:
```
mysql -u root -p
```
and then type this:
```
mysql> select Host,User from mysql.user;
```

---

### Post by thalon on 2008-10-22
After playing around with it for a while, here's my results:

```
ubuntu@ubuntu:~$ ping 192.168.144.32
PING 192.168.144.32 (192.168.144.32) 56(84) bytes of data.
64 bytes from 192.168.144.32: icmp_seq=1 ttl=64 time=0.115 ms
64 bytes from 192.168.144.32: icmp_seq=2 ttl=64 time=0.099 ms
64 bytes from 192.168.144.32: icmp_seq=3 ttl=64 time=0.099 ms

--- 192.168.144.32 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 1998ms
rtt min/avg/max/mdev = 0.099/0.104/0.115/0.011 ms
ubuntu@ubuntu:~$ mysql -h 192.168.144.32 -u root -p
Enter password:
ERROR 1045 (28000): Access denied for user 'root'@'192.168.144.21' (using password: YES)
ubuntu@ubuntu:~$ 
```

I can't seem to ping its hostname at all, at least the hostname I specified during the setup of the backend.  In Mythbuntu 8.04 do you have to set the hostname manually or something?  In any case, I got your suggested commands to work using the IP instead of the hostname.

And here's my proof that ports 6543 and 6544 are responding as normal:

```
ubuntu@ubuntu:~$ telnet 192.168.144.32 6543
Trying 192.168.144.32...
Connected to 192.168.144.32.
Escape character is '^]'.
kljdfl
Connection closed by foreign host.
ubuntu@ubuntu:~$ telnet 192.168.144.32 6544
Trying 192.168.144.32...
Connected to 192.168.144.32.
Escape character is '^]'.
Connection closed by foreign host.
ubuntu@ubuntu:~$ 
```

Okay, now onto the backend itself to poke around with permissions:

```
myuser@myth1:~$ mysql -u root -p mythconverg
Enter password: 
Reading table information for completion of table and column names
You can turn off this feature to get a quicker startup with -A

Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 151
Server version: 5.0.51a-3ubuntu5.1 (Ubuntu)

Type 'help;' or '\h' for help. Type '\c' to clear the buffer.

mysql> select Host,User from mysql.user;
+-------------+------------------+
| Host        | User             |
+-------------+------------------+
| %           | mythtv           | 
| %           | root             | 
| 127.0.0.1   | root             | 
| localhost   |                  | 
| localhost   | debian-sys-maint | 
| localhost   | mythtv           | 
| localhost   | root             | 
| ultramagnus |                  | 
| ultramagnus | root             | 
+-------------+------------------+
9 rows in set (0.01 sec)

mysql> quit
Bye
myuser@myth1:~$ 
```

Looks to me like root should be able to connect from anywhere, yet I'm still getting Access Denied.  Yes I tried multiple times to make sure it wasn't a fluke misspelling of the password...

Where do I go from here?  Thanks so much for your guys' help so far.



EDIT:  After all of that, I just tried resetting the mythtv password back to just 'mythtv' and it worked great.  I determined that for whatever reason the mysql command line password input prompt just doesn't like my keyboard's left shift key.  Go figure.

Ok this puts me in good shape, except I still don't know why I can't ping the primary backend by hostname.  Do these Mythbuntu boxes use DNS exclusively to resolve names or don't they do some sort of NetBIOS broadcast as a backup?  Pardon me, I guess I'm used to a Windows network.  If they just use DNS then I'd have to set up a DNS server in my home LAN just so they could register with it (currently my router just forwards DNS requests to my ISP's DNS servers).  Am I on the right track here?

---

### Post by uopjohnson on 2008-10-23
Ah the bad shift key error, I've actually had that one.  I wouldn't have thought of it though.  
DNS resolution is generally done/or not done by your router in a home network.  If you set dedicated dhcp addresses with host names it may or may not do local dns resolution for you.  In almost no cases will setting the hostname on the box itself work.
I hope that was vague enough, try poking around in your router config and see if there is a hostname box in there.

---

### Post by thalon on 2008-10-23
Yeah I've poked around in my router and all it does is pass along the DNS servers it gets from the WAN side to the DHCP scope on the LAN side.  Interestingly enough, I am able to ping the hostname from my Windows box and it resolves just fine, just not from a Mythbuntu environment.  Oh well, I guess I can just set up a caching DNS server internally here.

For those who haven't added a secondary backend yet and are wondering why I don't just use the IP everywhere, I tried both LiveCD and actually installing Mythbuntu to the hard drive, and it gets stuck at the exact same wizard screen.  It is a blue background, blue menus with white text.  First it asks language preference, then comes up with an automatically created list of backends (of course my list has only 1 entry).  But no matter if I hit OK or Configure Manually, it says it can't login to the database.  I believe this is because that screen is identifying the primary backend by hostname, but can't resolve the hostname to an IP address in order to ping it.  And the genius wizard won't let me Configure Manually if the ping doesn't work, so I'm in a catch-22 until the OS can reliably resolve the DNS hostname to its IP address.  Hmmm... might this be bug-report material?  If the Configure Manually button is useless because it won't let me configure it manually until it works correctly anyway?

---

### Post by anonymousdog on 2008-10-23
I setup dnsmasq on my backend (though I don't like to use its DHCP server functions -- isc-dhcp3 for me) for just this purpose.  It doesn't do dynamic registrations AFAIK, but does use the local hosts file entries; so, I just add needed name-to-IP entries there.

---

### Post by volkswagner on 2008-10-24
I never had a problem with the LiveCD connecting the my backend.  I use the ip address for the backend for setup.

From memory, I always had some sort of issue connecting to the backend, when setting ip address for MySQL location.  The best way for me was to leave the setting for "where MySQL Server resides" set to "Localhost".  This is how it still is.  

Once configured (not using liveCD) edit /etc/hosts.  This will allow you to use host names rather than ip address.

For all my Linux boxes, I edit /etc/host to include all machines on the LAN.

Example: /etc/hosts

```
127.0.0.1 localhost Machine1
192.168.1.107 Master
192.168.1.110 ServerMachine
00:18:XX:XX:XX:XX MyPhone
192.168.1.112 AnotherPC
192.168.1.117 YetAnother
192.168.1.108 Slave
192.168.1.103 WhySoManyPC
```

---

### Post by anonymousdog on 2008-10-24
> **volkswagner said:**
> For all my Linux boxes, I edit /etc/host to include all machines on the LAN.

Example: /etc/hosts

```
127.0.0.1 localhost Machine1
192.168.1.107 Master
192.168.1.110 ServerMachine
00:18:XX:XX:XX:XX MyPhone
192.168.1.112 AnotherPC
192.168.1.117 YetAnother
192.168.1.108 Slave
192.168.1.103 WhySoManyPC
```

...which you can do on just one box if you make that one the dnsmasq server and designate it as the DNS server in your DHCP server's configuration (so DHCP clients know where to look for DNS) and in /etc/resolv on any statically addressed clients.  /etc/host entries are slightly faster for the client to lookup but can become a bit of a management headache as the number of boxes on your LAN increases.

dnsmasq is so easy to use that it's a shame if you don't (unless you run full-blown DNS services locally).  In fact, I'd like to see it installed by default on master backends because it does no harm in any case: If you don't configure you LAN to use it, no clients look to it for DNS services, and it only acts as a local name-to-address cache for the machine on which it resides.  In fact, it probably would do no harm if installed by default for all Mythbuntu MythTV roles.

---

### Post by oobe-feisty on 2008-10-25
try starting mythbuntu-control-centre on the backend and make sure 
and make sure under system services you have mysql service enable over ethernet


you also need to run mythtv-setup on the backend and make sure the default ips on the first page of general setup are set to the lan ip of the back end the default value is 127.0.0.1

---

