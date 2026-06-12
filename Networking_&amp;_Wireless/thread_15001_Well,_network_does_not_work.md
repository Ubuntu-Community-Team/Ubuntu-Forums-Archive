---
title: "Well, network does not work"
date: 2005-02-11
forum: Networking &amp; Wireless
---

### Post by zwaps on 2005-02-11
Ok this might be a strange one.
First, I used the following partition scheme:
boot ext2, root reiserfs, two XFS /media and /media2 (entered it like this during install), reiserfs /home and 512MB /var ext3, boot 50mb, swap 256.
Dunno if this has anything to do with it, but it is the only thing I changed from other linux (gentoo to be precise) installs.
On the very top of boot I get an error that goes like "could not initialise ressource 4 at PCI device" or something, and I am afraid that maybe my harddisc is kinda broken (maybe?) Dunno.

Okay, during installation, dhcp worked fine. Found my Allied Telesyn 220E Router, installed software over the net.
Now, when I boot up my system, it DOES find the clockserver and gives me NO error whatsoever.
As soon as I am in Gnome, Network like ping or firefox does not work anymore.

When I use the Gnome Network tool something funny happens:
I can set the network manually or dhcp, but as soon as I click ok, the computer freezes completely.
Nothing works anymore, I have to reboot hard.

What could possibly be wrong with this piece of crap?
I am checking ifconfig now, but since I am writing with the livecd I can not give you that information just yet. I will, however, guess that eth0 ist configured correctly.
Should I enter my router as DNS server? Not that I didn't try but, oh well.

---

### Post by zwaps on 2005-02-11
root@trogdor:/home/zwaps # ifconfig eth0 192.168.1.1 netmask 255.255.255.0
root@trogdor:/home/zwaps # route add default gw 192.168.1.1
root@trogdor:/home/zwaps # ping [www.yahoo.com](www.yahoo.com)
ping: unknown host [www.yahoo.com](www.yahoo.com)
root@trogdor:/home/zwaps # ping 192.1681.1
ping: unknown host 192.1681.1
root@trogdor:/home/zwaps # ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=64 time=0.035 ms
64 bytes from 192.168.1.1: icmp_seq=2 ttl=64 time=0.035 ms
64 bytes from 192.168.1.1: icmp_seq=3 ttl=64 time=0.026 ms

--- 192.168.1.1 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2001ms
rtt min/avg/max/mdev = 0.026/0.032/0.035/0.004 ms
root@trogdor:/home/zwaps # ping -c 3 yahoo.com
ping: unknown host yahoo.com
root@trogdor:/home/zwaps # ifconfig
eth0      Protokoll:Ethernet  Hardware Adresse 00:0A:E4:43:03:71
          inet Adresse:192.168.1.1  Bcast:192.168.1.255  Maske:255.255.255.0
          inet6 Adresse: fe80::20a:e4ff:fe43:371/64 Gültigkeitsbereich:Verbindung
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000
          RX bytes:891 (891.0 b)  TX bytes:1045 (1.0 KiB)
          Interrupt:233 Basisadresse:0x1800

lo        Protokoll:Lokale Schleife
          inet Adresse:127.0.0.1  Maske:255.0.0.0
          inet6 Adresse: ::1/128 Gültigkeitsbereich:Maschine
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3163 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3163 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:0
          RX bytes:234989 (229.4 KiB)  TX bytes:234989 (229.4 KiB)

root@trogdor:/home/zwaps # route
Kernel IP Routentabelle
Ziel            Router          Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
default         192.168.1.1     0.0.0.0         UG    0      0        0 eth0

---

### Post by jubuntus on 2005-02-12
Check the sticky, you seem to be having the same problem as many?
[http://ubuntuforums.org/showthread.php?t=5690](http://ubuntuforums.org/showthread.php?t=5690)

---

### Post by alastair on 2005-02-12
If you cannot ping by a NAME, but can by an ADDRESS, then this points to name resolution issues i.e. DNS.

Check the /etc/resolv.conf

file. It should list the IP address of your DNS server(s).

---

