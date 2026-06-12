---
title: "No internet access."
date: 2012-09-18
forum: Mythbuntu
---

### Post by emedlin18 on 2012-09-18
emedlin@mythtv:/etc/network$ cat interfaces
auto lo
iface lo inet loopback
auto eth0
iface eth0 inet static
address 192.168.10.100
netmask 255.255.255.0
gateway 192.168.10.1

I can ping the router.
emedlin@mythtv:/etc/network$ ping  192.168.10.1
PING 192.168.10.1 (192.168.10.1) 56(84) bytes of data.
64 bytes from 192.168.10.1: icmp_req=1 ttl=64 time=0.318 ms
64 bytes from 192.168.10.1: icmp_req=2 ttl=64 time=0.302 ms
64 bytes from 192.168.10.1: icmp_req=3 ttl=64 time=0.377 ms
^C
--- 192.168.10.1 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 1999ms
rtt min/avg/max/mdev = 0.302/0.332/0.377/0.035 ms

I can ping my cable modem.
emedlin@mythtv:/etc/network$ ping 192.168.100.1
PING 192.168.100.1 (192.168.100.1) 56(84) bytes of data.
64 bytes from 192.168.100.1: icmp_req=1 ttl=63 time=1.92 ms
64 bytes from 192.168.100.1: icmp_req=2 ttl=63 time=1.90 ms
64 bytes from 192.168.100.1: icmp_req=3 ttl=63 time=1.96 ms
^C
--- 192.168.100.1 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2009ms
rtt min/avg/max/mdev = 1.908/1.932/1.964/0.023 ms

All though it looks like this machine cannot get out to the net for some reason.
emedlin@mythtv:/etc/network$ telnet time-a.nist.gov 13 telnet: could not resolve time-a.nist.gov/13: Name or service not known

Also sudo apt-get update produces alot of Failed to fetch... lines.

What could be blocking me if I can get to the cable modem?  I know it worked a few days ago when I did the fresh install.  Since then I have changed it to use a static ip and made a change to grub that is causing alot of problems.  See my "Grub problem" thread for that part.  /etc/network/interfaces is the only file I changed to make it use a static ip.

---

### Post by nickrout on 2012-09-18
Looks like your DNS is not set up properly.

First can you ping an internet IP address, eg ```
ping 203.97.30.187
```

---

### Post by emedlin18 on 2012-09-18
Yes.

emedlin@mythtv:~$ ping 203.97.30.187
PING 203.97.30.187 (203.97.30.187) 56(84) bytes of data.
64 bytes from 203.97.30.187: icmp_req=1 ttl=46 time=219 ms
64 bytes from 203.97.30.187: icmp_req=2 ttl=46 time=219 ms
64 bytes from 203.97.30.187: icmp_req=3 ttl=46 time=220 ms
^C
--- 203.97.30.187 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2016ms
rtt min/avg/max/mdev = 219.101/219.615/220.151/0.428 ms

---

### Post by nickrout on 2012-09-18
> **emedlin18 said:**
> Yes.

emedlin@mythtv:~$ ping 203.97.30.187
PING 203.97.30.187 (203.97.30.187) 56(84) bytes of data.
64 bytes from 203.97.30.187: icmp_req=1 ttl=46 time=219 ms
64 bytes from 203.97.30.187: icmp_req=2 ttl=46 time=219 ms
64 bytes from 203.97.30.187: icmp_req=3 ttl=46 time=220 ms
^C
--- 203.97.30.187 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2016ms
rtt min/avg/max/mdev = 219.101/219.615/220.151/0.428 ms
There you are, nothing is blocking you, you have internet access but no DNS service by the look of it. 

I see you are using /etc/network/interfaces to get your network settings. Assuming you are on 12.04 the whole dns setup has changed, but I think you need to look at the first Q&A on this page:

[http://www.stgraber.org/2012/02/24/dns-in-ubuntu-12-04/](http://www.stgraber.org/2012/02/24/dns-in-ubuntu-12-04/)

Frankly you are probably better to get your network setup via dhcp, but if you insist on /etc/network/interfaces then you have to specify your dns settings as per the referenced page.

---

### Post by emedlin18 on 2012-09-18
Thanks.  I will look at that page.  I need a static ip since this is a server.

---

### Post by nickrout on 2012-09-18
> **emedlin18 said:**
> Thanks.  I will look at that page.  I need a static ip since this is a server.The other option is to get your dhcp server to serve the same address to your sever each time, that's what i do.

---

### Post by emedlin18 on 2012-09-18
I tried that when I was running 10.04 and it never worked.  I don't know if it was 10.04 problem or a router problem.  It would always get a random ip from dhcp.  I ended up just telling the machine to use a static ip outside the dhcp range in 10.04 and it worked fine.  12.04 seems to work differently.

---

### Post by emedlin18 on 2012-09-18
Added dns-nameservers 8.8.8.8 192.168.10.1 to /etc/network/interfaces then ran sudo ifdown eth0; sudo ifup eth0; and it works.

---

### Post by nickrout on 2012-09-18
great, it's working, that's what counts.

PS my 10.04 boxes work ok with "fixed" dhcp addresses, so it must have been a router or setup problem :)

---

