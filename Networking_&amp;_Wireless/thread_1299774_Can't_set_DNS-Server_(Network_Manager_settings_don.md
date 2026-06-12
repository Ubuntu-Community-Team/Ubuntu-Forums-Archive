---
title: "Can't set DNS-Server (Network Manager settings don't work)"
date: 2009-10-24
forum: Networking &amp; Wireless
---

### Post by slabo on 2009-10-24
Hello!

Using the DNS on my router leads to a lag of about 3-5 sec. per query. This seems to be a known problem with the router. I can't disable the DNS-Server on the router. So, i tried to set another DNS-Server, but even though the gnome-network-manager shows it correct, it doesn't work.

Some diagnostics:

```
...@urania:~$ '''uname -a'''
Linux urania 2.6.28-15-generic #49-Ubuntu SMP Tue Aug 18 19:25:34 UTC 2009 x86_64 GNU/Linux

...@urania:~$ '''egrep -v "^$|^#" /etc/network/interfaces'''
auto lo
iface lo inet loopback
auto eth0
iface eth0 inet dhcp
dns-nameservers 213.73.91.35 

...@urania:~$ '''egrep -v "^$|^#" /etc/resolv.conf'''
nameserver 129.70.240.53
nameserver 129.70.182.8
nameserver 192.168.178.1
search uni-bielefeld.de

(Anmerkung: Die ersten beiden Nameserver gehören wohl zur Uni Bielefeld, wohin ich mal ein VPN aufgebaut hatte. Bei dem anderen Rechner ist das aber nicht passiert, aber er hat dasselbe Problem, s.o., ich glaube also, diese Spuren (von KVPN glaube ich) können ignoriert werden.)

...@urania:~$ '''egrep -v "^$|^#" /etc/hosts'''
127.0.0.1	localhost
127.0.1.1	urania
192.168.178.20	urania	
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

...@urania:~$ '''ifconfig'''
eth0      Link encap:Ethernet  HWaddr 00:1f:d0:92:47:bc  
          inet addr:192.168.178.21  Bcast:192.168.178.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:d0ff:fe92:47bc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6697 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7044 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5330886 (5.3 MB)  TX bytes:1347899 (1.3 MB)
          Interrupt:253 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

...@urania:~$ '''route -n'''
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.178.0   0.0.0.0         255.255.255.0   U     1      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.178.1   0.0.0.0         UG    0      0        0 eth0
0.0.0.0         192.168.178.1   0.0.0.0         UG    100    0        0 eth0

...@urania:~$ '''iwconfig'''
lo        no wireless extensions.
eth0      no wireless extensions.
pan0      no wireless extensions.
```

Somhow i get the impression, that some other program than network manager is handling my internet connection, because next to the connection, nm says it never used it. At least, that's how i understand that "never":

[IMG]http://img98.imageshack.us/img98/1466/screenshotnetworkconnec.png[/IMG]

Any ideas how i could find out what software is handling the connection and how i could enforce the settings in the network manager?

---

### Post by Iowan on 2009-10-24
Your definition in */etc/network/interfaces* overrides NM. 
Using DHCP, you might try [this]("http://ubuntuforums.org/showpost.php?p=8157119&postcount=3").

---

### Post by slabo on 2009-11-02
A late thx for the answer. Somehow i didn't get it working, but the upgrade to 9.10 did it. Resolved for me.

---

