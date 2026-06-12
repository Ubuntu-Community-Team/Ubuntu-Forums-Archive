---
title: "Problem with 2 networks interfaces."
date: 2010-01-29
forum: Networking &amp; Wireless
---

### Post by puimino on 2010-01-29
Hi!  i have a   annoying  issue,

first i 'am using ubuntu jaunty on my   laptop acer aspire 4530
second i have 2 networks:

network 1 is wireless  and their ip is 192.168.1.12/24 this ip is assigned dinamically.

network 4 is wired and their ip is  192.168.4.56/24 is  manually assigned.



if only  have attached the network 1 i have  internet access and to others  pc on the net but  when cable of the network 4  is attached i lost the connection to  network 1

ping 192.168.1.10
PING 192.168.1.10 (192.168.1.10) 56(84) bytes of data.
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permit


then i detach the wire of network 4  and immediatelly

64 bytes from 192.168.1.10: icmp_seq=14 ttl=128 time=8.83 ms
64 bytes from 192.168.1.10: icmp_seq=15 ttl=128 time=1.70 ms
64 bytes from 192.168.1.10: icmp_seq=16 ttl=128 time=1.63 ms
64 bytes from 192.168.1.10: icmp_seq=17 ttl=128 time=1.67 ms



posible is the route table  is missconfigured but i dont know how can fix this ...

---

### Post by Iowan on 2010-01-30
First, are both interfaces configured via Network Manager? NM usually only activates one interface at a time (although my Jaunty laptop occasionally has both) - and it apparently favors the faster connection. Otherwise, you can check **route -n** with/out cable connected - and see if anything changes.

(The "ping: sendmsg: Operation not permitted" is kinda interesting - I'm seeing this in another thread.)

---

### Post by 2hot6ft2 on 2010-01-30
Looks like you're having the same issue as I am in this thread.
[Ubuntu 2 Ubuntu via Ethernet while still using WiFi?]("http://ubuntuforums.org/showthread.php?p=8748824")

No solution as of yet but maybe you'll get some insight there and see what has been tried.

Are you connecting 2 pc's together by the Ethernet cable like I am?
If so does one or both pc's have a gigabit Ethernet adapter?
If not you'll either have to use a crossover cable or a router/hub with regular cat5 Ethernet patch cables.

---

### Post by puimino on 2010-02-02
yes, the Network manager is setting  both networks...

---

### Post by puimino on 2010-02-02
[QUOTE=2hot6ft2;8748869]Looks like you're having the same issue as I am in this thread.
[Ubuntu 2 Ubuntu via Ethernet while still using WiFi?]("http://ubuntuforums.org/showthread.php?p=8748824")

ok, i will check this thread..

---

### Post by Skaperen on 2010-02-02
It looks like NM is the culprit here, and for other problems such as leaving a computer with wireless accessible for remote logins while no one is logged in on the console. What I'd like to do in my case is just get network manager to go away. Who knows the best clean way to do that? Uninstall it abd just let startup script configure everything?

It would still be nice to be able to quickly make use of other wireless and wired networks when mobile.

---

### Post by Iowan on 2010-02-02
There are ways to disable NM without removing it. You *should* be able to define your wireless in */etc/network/interfaces* - NM should leave it alone, and it should activate at bootup (whereas NM requires login). A couple of threads have done this - but NM still exerts it's influence. NM can be disabled via Preferences>Startup Applications. Looks like it could be removed there as well, but going back is difficult.

---

