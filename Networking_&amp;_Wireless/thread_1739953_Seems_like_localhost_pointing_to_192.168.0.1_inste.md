---
title: "Seems like localhost pointing to 192.168.0.1 instead of 127.0.0.1"
date: 2011-04-26
forum: Networking &amp; Wireless
---

### Post by enthree on 2011-04-26
Hello everyone,

When i try to connect to MySQL database with MySQL Workbench using root@localhost i get following message:
Failed to Connect to MySQL at localhost:3306 with user root
Access denied for user 'root'@'192.168.0.1' (using pasword: YES)

...which is ok, becouse 192.168.0.1 is not listed as a host from which MySQL server should accept connections.

I am a little confused, becouse i tell MySQL Workbench to connect using localhost, so server should (at least i think so) receive connection from 127.0.0.1

I think i had similar issue with PostgreSQL some time ago, but i just allowed connections from 192.168.0.1 then.

My host file is:
```
127.0.0.1       localhost
127.0.0.1       localhost.localdomain   localhost
#::1    ent-pc  localhost6.localdomain6 localhost6
127.0.0.1       ent-pc

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```My interfaces:
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet manual

pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf

auto dsl-provider
iface dsl-provider inet ppp
provider dsl-provider

auto eth1 eth1:1
iface eth1 inet static
        address 192.168.0.1
        network 192.168.0.0
        netmask 255.255.255.0
iface eth1:1 inet static
        address 192.168.1.103
        network 192.168.1.0
        netmask 255.255.255.0
        gateway 192.168.1.1
```
Any thoughts? :)
Same thing happens when i try to use root@127.0.0.1 -> Access denied for user 'root'@'192.168.0.1'

enthree.

---

### Post by Iowan on 2011-04-26
I ordinarily leave 127.0.0.1 with the "localhost" alias.  I associate the machine name with 127.0.1.1
(Although I have a server with machine name tied to 192.168.X.X address)

---

### Post by enthree on 2011-04-27
Thanks for Your reply, Iowan.

The question is why MySQL Server is receiving a connection from MySQL Workbench from 192.168.0.1 instead of 127.0.0.1. My [COLOR=Red]guts[/COLOR] tell me its becouse of Ubuntu configuration (thats why i ask here, not MySQL forums). :/


[COLOR=Red][typo][/COLOR]

---

### Post by Maheriano on 2011-04-27
If you didn't already know, 192.168.0.1 is the local IP of DLink switches. So that's your local network's home IP I guess.

---

### Post by enthree on 2011-04-28
Yes it is, Maheriano.

That's my setup, so my wifi devices (laptop, phone) can use server dhcp through my access point working as a switch for network 192.168.0.0 and as a router for network 192.168.1.0 (so i can get to access point's config page).

As far as i know if i use 127.0.0.1 (loopback) - connection does not need to go through some of the system routines. Thats why i would like to connect with PHP and MySQL Workbench to MySQL server using 127.0.0.1. Unfotunatly server receives connection at 192.168.0.1 when i use 127.0.0.1.

When  i set connection permissions for a MySQL user to 127.0.0.1, there is no way for him to successfully connect.

Maybe i'm missing something here.

Thanks for reading.

---

### Post by chili555 on 2011-04-28
I think Iowan and I would be interested to know if the behavior changes if you amend:```
127.0.0.1       localhost
127.0.0.1       localhost.localdomain   localhost
#::1    ent-pc  localhost6.localdomain6 localhost6
127.0.[COLOR="Red"]**1**[/COLOR].1       ent-pc

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```Reboot in order to restart networking, sql, and everything else. Any improvement?

---

### Post by BrotenAaron on 2012-06-20
A drawback linked to just about all personal IPs will be the truth those create the internet connection non-routable with no NAT. Additionally, a number of people like 192.168.1.1 as a possible Ip as it has been seen for being very great for a steady exchange of info by the link. You can also have the identical value like the number designed for the link gateway, even while creating the Ip address attributes. The readily accessible aspect of this particular IP may also turn into a negative aspect if someone demands a little something a much more secure and safe. A thing that must be pointed out at this point is that utilizing 192.168.1.1 is regarded as to generally be very secure as it could make you much less susceptible to safety risks within the net. In terms of [192-168-01.com]("http://www.192-168-01.com/") an individual's odds of getting aid on the web is quite significant due to the extensive make use of all around the globe.

Realizing the Ip gets to be a requirement especially when you plan to arrange and attach a modem. In case the Internet Protocol address of an individual's modem is certainly 192.168.1.1 now the initial step for taking is to type [http://192.168.1.1/](http://192.168.1.1/) in the browser’s address bar thus hitting enter on the key pad. If your web browser brings you to the Logon page, type in the appropriate information as well as enter onto the admin's control unit. There you'll find the setting configurations. Get the needed adjustments ahead of saving and also leaving. When the situation is specifically broken to your benefit, you will have to determine the complication as well as trobleshoot and fix appropriately.

---

