---
title: "SIOCADDRT: no such process. frustrating error. (Static Ip)"
date: 2010-01-21
forum: Networking &amp; Wireless
---

### Post by Nano3.14 on 2010-01-21
getting an annoying error here after trying to set up a static ip connection through eth0, 
 after running sudo /etc/init.d/networking restart, and havent found a good answer anywhere on the fora here.

```
*Reconfiguring network interfaces...
SIOCADDRT: No such process
Failed to bring up eth0.
[OK]
```The relevant part of the /etc/network/interfaces follows:

```
auto eth0
iface eth0 inet static
           address 192.168.1.221
           netmask 255.255.255.0
           network 192.168.0.0
           broadcast 192.168.1.255
           gateway 192.168.0.1 
```anyone have any idea at all what could be wrong?

---

### Post by chili555 on 2010-01-21
> address 192.168.1.221
           netmask 255.255.255.0
           network 192.168.0.0
           broadcast 192.168.1.255
           gateway 192.168.0.1I don't think you can find 192.168.[COLOR="Red"]1[/COLOR].221 in a 192.168.[COLOR="Red"]0[/COLOR].0 network. Assuming your router is actually 192.168.1.1, then I would change your file to:```
address 192.168.1.221
netmask 255.255.255.0
gateway 192.168.1.1
```Restart networking and you should be good to go.

---

### Post by Nano3.14 on 2010-01-21
well wow. that was a really stupid error on my part, ha. it turns out the router address was correct and i just wasnt paying attention to the address. 
anyway, now i restart the networking and get no errors, but my router doesnt register me as being connected, meaning that even if i am connected i cant port-forward. 
[COLOR=Black]nevertheless, ifconfig thinks im connected, and i can ping google.com with no trouble. so this would just be a problem with my router, i presume?
edit: well the infinte loop pinging thing was just me being ignorant of ctrl-c, so disgregard that...
[/COLOR]

---

### Post by chili555 on 2010-01-21
> the infinte loop pinging thing was just me being ignorant of ctrl-c, so disgregard that...You could also try:```
ping -c3 www.google.com
```That is, for a count of 3 and then stop.>  i can ping google.com with no trouble. Then you are connected just fine, no matter what the router thinks.

Did you fix up /etc/resolv.conf?

---

### Post by Nano3.14 on 2010-05-31
well, i dont want to jack this thread, but im having the same problem. here is my ifconfig -a and /etc/network/interfaces:

```

eth0   Link encap:Ethernet  HWaddr 00:14:85:68:63:4c
         inet addr:192.168.1.221 Bcast:192.168.1.225  Mask:225.225.225.0
         inet6 addr: fe80::214:85ff:fe68:634e/64 Scope:link
         UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
         RX packets:596 errors:0 dropped:0 overruns:0 frame:0
         TX packets:478 errors:0 dropped:0 overruns:0 carrier:0
         collisions:0 txqueuelen:1000
         RX bytes:54246 (54.2 KB)  TX bytes:29630 (29.6 KB)
         Interrupt:17 Base address:0x3800

```
```

auto eth0
iface eth0 inet static
           address 192.168.1.221
           netmask 225.225.225.0
           network 192.168.1.1
           broadcast 192.168.1.225
           gateway 192.168.0.1

```
as you can see i only included the parts that seemed to be relevant (basically didnt include any of the loopback stuff, this was copied by hand)


thanks!

---

### Post by Iowan on 2010-05-31
Moved post here from year-old thread.

---

