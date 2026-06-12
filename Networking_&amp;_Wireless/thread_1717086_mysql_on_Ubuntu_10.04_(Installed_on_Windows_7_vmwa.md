---
title: "mysql on Ubuntu 10.04 (Installed on Windows 7 vmware)"
date: 2011-03-29
forum: Networking &amp; Wireless
---

### Post by nixnet on 2011-03-29
Hi,

I have installed Ubuntu 10.04 desktop edition on vmware (Windows 7). In this I have configured MySQL server which works flawless while connecting from client within ubuntu box.

The IP address & port is 192.168.38.131:3306.
(Vmware network: NAT
VMware Network Adapter VMnet8: 192.168.38.1)

However, when I try to connect from windows host, following is the error.
Command 1:
mysql -h 192.168.38.131 -u root -p
Enter password: ****
ERROR 1130 (HY000): Host '192.168.38.1' is not allowed to connect to this MySQL
server

Command 2:
mysqladmin ping -h 192.168.38.131 -u root -p
Enter password: ****
mysqladmin: connect to server at '192.168.38.131' failed
error: 'Host '192.168.38.1' is not allowed to connect to this MySQL server'

Above commands work just fine from Ubuntu itself.

Any comments on how to resolve this?

Thanks in advance!! :)

---

### Post by SeijiSensei on 2011-03-29
What's the value of "bind-address" in my.cnf?  If it's 127.0.0.1, the default, the server is only listening on the local interface.  You can replace that with "192.168.38.131" so it listens on the emulated Ethernet interface. Or you can remove it or comment it out to have mysqld listen on all interfaces.

You may also need to GRANT access to IP addresses in 192.168.38.0/24 in the MySQL server itself.

---

### Post by nixnet on 2011-03-30
Thanks Seiji,

I have already configured "bind-address" in my.cnf to 192.168.38.131 and given grants to database for user@192.168.38.131.
I am already able to connect from local Ubuntu box with following.
"mysql -h 192.168.38.131 -u username -p"

The problem is only while connecting from remote client.

Strangely, even while specifying "-h **192.168.38.1[COLOR=Red]31[/COLOR]**"(Ubuntu Box IP) it gives error for "**192.168.38.1**" which is IP address of "VMware Network Adapter VMnet8".

Any idea how can this be solved?

---

### Post by nixnet on 2011-03-30
Gave GRANTS to user for IP 192.168.38.1 while "bind-address=192.168.38.131".

This worked. I am now able to connect form remote clients as well.

---

