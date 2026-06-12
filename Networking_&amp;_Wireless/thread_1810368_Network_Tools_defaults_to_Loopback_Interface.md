---
title: "Network Tools defaults to Loopback Interface"
date: 2011-07-22
forum: Networking &amp; Wireless
---

### Post by reveponym on 2011-07-22
I'm running Ubuntu 11.04 and I've been unable to access any type of Internet service besides web browsing.

When I check on Network Tools, it's always set on Loopback Interface, regardless of whether I've just switched it to Ethernet Interface. I haven't been able to download system updates through Update Manager.

I'm not very experienced with Ubuntu, so noob help plz. Thanks!

---

### Post by papibe on 2011-07-22
Could you post an screenshot of how it is configured your network in the network manager (the IPv4 Settings tab would be perfect)?

Also could you post the result of these 2 commands?
```
$ ifconfig

$ route -n
```
Regards.

---

### Post by reveponym on 2011-07-23
Thanks for the quick and helpful reply. 

I've considered that the networking hardware may be going out, the motherboard is pretty old.

Here are the command results.

ifconfig
```
eth0      Link encap:Ethernet  HWaddr 00:e0:06:09:06:fa
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:6ff:fe09:6fa/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:24923 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12612 errors:0 dropped:1 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:26773569 (26.7 MB)  TX bytes:1881354 (1.8 MB)
          Interrupt:19 Base address:0xd400

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:50 errors:0 dropped:0 overruns:0 frame:0
          TX packets:50 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:3798 (3.7 KB)  TX bytes:3798 (3.7 KB)

```route -n
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
```

And the Network Tools window. Please note that this is how I found it, I have not changed anything in this window.

[ATTACH]198131[/ATTACH]

---

### Post by papibe on 2011-07-23
'ifconfig' and 'route' looks OK. That is, you have an LAN IP, mask, gateway and default route.

Maybe it is a DNS problem?  Are you able to resolve names? For example, What is the result of these commands?
```
$ nslookup google.com

$ dig google.com
```
Regards.

BTW, I meant the a screenshot of Network Connections -> Wired -> eth0 -> edit -> IPv4 Settings.

---

### Post by reveponym on 2011-07-23
IPv4 setings for the eth0 connection are simply 'Automatic (DHCP)', which is what I would expect.

I have other machines running Windows connected to the same router, and they are not having any difficulty.

I am posting this from the machine which is having trouble, so web connectivity is not an issue.

```

 nslookup google.com
Server:         192.168.1.1
Address:        192.168.1.1#53

Non-authoritative answer:
Name:   google.com
Address: 74.125.227.83
Name:   google.com
Address: 74.125.227.82
Name:   google.com
Address: 74.125.227.84
Name:   google.com
Address: 74.125.227.80
Name:   google.com
Address: 74.125.227.81

dig google.com

; <<>> DiG 9.7.3 <<>> google.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 52431
;; flags: qr rd ra; QUERY: 1, ANSWER: 5, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;google.com.                    IN      A

;; ANSWER SECTION:
google.com.             91      IN      A       74.125.227.48
google.com.             91      IN      A       74.125.227.50
google.com.             91      IN      A       74.125.227.49
google.com.             91      IN      A       74.125.227.52
google.com.             91      IN      A       74.125.227.51

;; Query time: 15 msec
;; SERVER: 192.168.1.1#53(192.168.1.1)
;; WHEN: Sat Jul 23 02:08:54 2011
;; MSG SIZE  rcvd: 108


```

---

### Post by papibe on 2011-07-23
It looks like everything is working from the command line.

Are you able to browse the Internet using your browser?
What kind of error do you get when updating?

Regards.

---

### Post by reveponym on 2011-07-24
Update Manager starts to download, then gets this.

[ATTACH]198243[/ATTACH]


I had another program which had a Name Resolution error last week, but now works fine. I thought the two might be related, and checked Network Tools to see, and thought the Loopback setting might be a problem causing both of those. Now I'm not so sure.

---

### Post by papibe on 2011-07-24
I took a second look at this:
> **reveponym said:**
> 
ifconfig
```
eth0      Link encap:Ethernet  HWaddr 00:e0:06:09:06:fa
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:6ff:fe09:6fa/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  [COLOR="Red"]**MTU:1500**[/COLOR]  Metric:1
          RX packets:24923 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12612 errors:0 dropped:1 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:26773569 (26.7 MB)  TX bytes:1881354 (1.8 MB)
          [COLOR="Red"]**Interrupt:19 Base address:0xd400**[/COLOR]
```
That is not completely right. Try this:
```
$ sudo ifconfig eth0 down
$ sudo ifconfig eth0 mtu 1024
$ sudo ifconfig eth0 up
```
Try some browsing and maybe update (not upgrade yet), and report back.

Regards.

---

### Post by reveponym on 2011-07-26
Excellent! That's got Update Manager working again. Thanks so much!

---

### Post by papibe on 2011-07-26
In order to make those settings permanent go to Network Connections, select eth0, edit, and then set the MTU value as in the attached picture.

Regards.

---

