---
title: "Backend server setup questions"
date: 2008-05-03
forum: Mythbuntu
---

### Post by andyd273 on 2008-05-03
I'm a Linux newbie, and I've already had to reformat and start installing from scratch once, so I'm going to ask for help this time.

1. Is there a way to make a backup of how I have it all configured now, so that if I mess it up again I won't have to redo all this updating and stuff again?

2. I want to set up the back end so that I can connect to it from another computer (one with tv out) or maybe even my soft modded XBox. But I don't know how to set a static IP. The cheap netgear router I have wont let me assign an IP by mac address, so where do I set it in ubuntu? and what do I have to do to make mythtv work with a static IP?

3. How do I change the back end database password? Right now it is some random characters, which I will never remember. Is there a fool proof way to change it and not mess everything up?
(this is what I was trying to do when I messed it all up last time).

---

### Post by ian dobson on 2008-05-04
Hi,

1) You can backup your settings/MythTV configuration using mysqldump, with something like:-

mysqldump -uUSER -pPASSWORD --all-databases --opt | bzip2 > /data/backup-sql.bz2

This will create a compressed dump of your complete Sql database to /data/backup-sql.bz2

2) YOu can configure a "hardwired" IP addresss by editing the /etc/network/interface file. My file looks as follows:-
# The loopback network interface
```

auto lo eth1
iface lo inet loopback

# The primary network interface
iface eth0 inet dhcp

iface eth1 inet static
address 192.168.0.1
netmask 255.255.255.0
broadcast 192.168.0.255
gateway 192.168.0.254

auto eth1:0
iface eth1:0 inet static
address 192.168.0.2
netmask 255.255.255.0
broadcast 192.168.0.255

```
Note I have 2 static IP addresses for eth1 and eth0 is only used sometimes and uses DHCP.

3) You can change the password for Myth in the mythtv-setup program. You'll also need to edit the mysql.txt which is usually in the home directory then /.mythtv/mysql.txt.

Hope this helps
Regards
Ian Dobson

---

