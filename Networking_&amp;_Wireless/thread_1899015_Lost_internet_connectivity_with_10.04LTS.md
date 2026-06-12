---
title: "Lost internet connectivity with 10.04LTS"
date: 2011-12-22
forum: Networking &amp; Wireless
---

### Post by JohnsonMR on 2011-12-22
I have lost all external connectivity but I still have access to and from other systems on my local network.  I think I lost it on a previous update.  I can not longer download updates, search the internet or ping google.com.  I can boot that desktop using a 10.04 LTS CD and everything works fine.  Based on that I'm assuming it's a local software problem and not hardware or router issue.

First thing I'd like to do is boot up under one of the previous kernels (I know I have 3-4 of them) but Grub in not displaying anything on boot up so I can do this.  I do I fix that?

If booting up under a previous kernel does not work what should I look at next to resolve this issue.

If all else fails, then I'll just reinstall everything.  I'd like to avoid that if I can.

---

### Post by jonobr on 2011-12-22
can you ping 74.125.224.80

can you put it in a browser?
does that work?

If it does, post the results of /etc/resolv.conf
and /etc/nsswitch.conf

---

### Post by JohnsonMR on 2011-12-22
Pinging 74.125.224.80 from Firefox gives me "Server not found".

---

### Post by jonobr on 2011-12-22
what does your ifconfig and /etc/network/interfaces file look like?

---

### Post by JohnsonMR on 2011-12-22
ifconfig:

eth0      Link encap:Ethernet  HWaddr 00:15:58:71:f1:e5  
          inet addr:192.168.0.50  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::215:58ff:fe71:f1e5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:149 errors:0 dropped:0 overruns:0 frame:0
          TX packets:235 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:14307 (14.3 KB)  TX bytes:33691 (33.6 KB)
          Interrupt:20 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:151 errors:0 dropped:0 overruns:0 frame:0
          TX packets:151 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15826 (15.8 KB)  TX bytes:15826 (15.8 KB)

/etc/network/interfaces:

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.0.50
netmask 255.255.255.0
network 192.168.0.0
broadcast 192.168.0.255
gateway 192.168.0.1

---

### Post by jonobr on 2011-12-22
> RX packets:149 errors:0 dropped:0 overruns:0 frame:0
TX packets:235 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:14307 (14.3 KB) TX bytes:33691 (33.6 KB)
Interrupt:20 Base address:0x2000 

Ifconfig seems to show your interface is up and has an IP address,
and the above quote seems to show traffic.

Can you ping 192.168.0.50 and then 192.168.0.1?

Can you ping any other devices on the same network?

---

### Post by praseodym on 2011-12-22
Hi,

change the value from "false" to "true" in the file **/etc/NetworkManager/nm-system-settings.conf** otherwise the networkmanager and the manual config disturb each other

---

### Post by JohnsonMR on 2011-12-22
> **jonobr said:**
> Ifconfig seems to show your interface is up and has an IP address,
and the above quote seems to show traffic.

Can you ping 192.168.0.50 and then 192.168.0.1?

Can you ping any other devices on the same network?

yes.  192.168.0.1 is my router and I can run the admin routines.  I can ping myself (192.168.0.50) and other devices on my local network.  192.168.0.50 has my shared printers on it and some local shares and I can print and mount these shares from anyone of 5 other devices on my local network.

I have also bypassed my router and connected directly to the cable modem ans still can't access anything on the external network from this device.

---

### Post by JohnsonMR on 2011-12-22
> **praseodym said:**
> Hi,

change the value from "false" to "true" in the file **/etc/NetworkManager/nm-system-settings.conf** otherwise the networkmanager and the manual config disturb each other

Changed it from false to true and rebooted.  No change.

---

### Post by praseodym on 2011-12-22
Take router/modem/splitter/computer/etc. off the current for about 10 minutes and try it again. Router firmware is up-to-date?

---

### Post by jonobr on 2011-12-22
recommend opening a terminal

```
sudo tcpdump -n -s 1600 -i any udp port 53
```

then either do
```
nslookup google.com
```
or google ina browser

post results here

---

### Post by JohnsonMR on 2011-12-22
No change after a power down of router/modem/computer.  I updated the firmware in the router about two weeks ago.  I've had this problem for 2-3 months.

I have 6 other computers on this network, some running 10.04lts also and this one computer is the only one with the problem.

---

### Post by jonobr on 2011-12-23
Hello


Any luck with the tcpdump??

---

### Post by JohnsonMR on 2011-12-23
> **jonobr said:**
> recommend opening a terminal

```
sudo tcpdump -n -s 1600 -i any udp port 53
```

then either do
```
nslookup google.com
```
or google ina browser

post results here

Here it is:

tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on any, link-type LINUX_SLL (Linux cooked), capture size 1600 bytes
09:48:09.012993 IP 127.0.0.1.53974 > 127.0.0.1.53: 57803+ A? google.com. (28)
09:48:10.013092 IP6 ::1.38283 > ::1.53: 57803+ A? google.com. (28)
09:48:15.013103 IP 127.0.0.1.53974 > 127.0.0.1.53: 57803+ A? google.com. (28)
09:48:16.013268 IP6 ::1.38283 > ::1.53: 57803+ A? google.com. (28)
09:48:21.013401 IP 127.0.0.1.53974 > 127.0.0.1.53: 57803+ A? google.com. (28)
09:48:22.013552 IP6 ::1.38283 > ::1.53: 57803+ A? google.com. (28)
09:51:48.579230 IP 127.0.0.1.41813 > 127.0.0.1.53: 28152+ A? 174,125.224.80. (32)
09:51:49.579341 IP6 ::1.50369 > ::1.53: 28152+ A? 174,125.224.80. (32)
09:51:54.579355 IP 127.0.0.1.41813 > 127.0.0.1.53: 28152+ A? 174,125.224.80. (32)
09:51:55.579536 IP6 ::1.50369 > ::1.53: 28152+ A? 174,125.224.80. (32)
09:52:00.579686 IP 127.0.0.1.41813 > 127.0.0.1.53: 28152+ A? 174,125.224.80. (32)
09:52:01.579861 IP6 ::1.50369 > ::1.53: 28152+ A? 174,125.224.80. (32)

---

### Post by jonobr on 2011-12-23
Hello


I may be reading this wrong but your machine initially does a query from
127.0.0.1 to 127.0.0.1 (itself) for google.
Then there appears to be an IPv6 query looking for google as well,
this happens a couple of times?

This implies that maybe your running DNS on that server and looking up on that server?


There is a response eventually saying that google is at  174,125.224.80.
which is incorrect
Google is at 74.125.224.80

notice the comma in the first result and then 1 at the start.

I may have to do a tcpdump myself on command line and compare against your result

---

### Post by praseodym on 2011-12-23
Please check 

> cat /etc/hosts

---

### Post by jonobr on 2011-12-23
> listening on any, link-type LINUX_SLL (Linux cooked), capture size 65535 bytes
09:10:01.201071 IP ubuntu.41576 > home.domain: 34055+ A? google.com. (28)
09:10:01.202137 IP ubuntu.46044 > home.domain: 52052+ PTR? 254.1.168.192.in-addr.arpa. (44)
09:10:01.230433 IP home.domain > ubuntu.46044: 52052* 1/1/1 PTR home. (172)
09:10:01.230830 IP ubuntu.46436 > home.domain: 52323+ PTR? 66.1.168.192.in-addr.arpa. (43)
09:10:01.243674 IP home.domain > ubuntu.46436: 52323* 1/1/1 PTR ubuntu. (171)
09:10:01.244194 IP home.domain > ubuntu.41576: 34055 5/0/0 A 74.125.224.81, A 74.125.224.80, A 74.125.224.82, A 74.125.224.84, A 74.125.224.83 (108)



tcpdump on my system above shows the correct answers, again, im not sure why your query goes to 127.0.0.1, again, maybe your hosting your won dns

Also , if the hosts was doing the resolving, the port 53 packet would never hit the interface,

---

### Post by JohnsonMR on 2011-12-23
> **jonobr said:**
> Hello


I may be reading this wrong but your machine initially does a query from
127.0.0.1 to 127.0.0.1 (itself) for google.
Then there appears to be an IPv6 query looking for google as well,
this happens a couple of times?

This implies that maybe your running DNS on that server and looking up on that server?


There is a response eventually saying that google is at  174,125.224.80.
which is incorrect
Google is at 74.125.224.80

notice the comma in the first result and then 1 at the start.

I may have to do a tcpdump myself on command line and compare against your result




Sorry, I ran the nslookup twice; one as google.com and the other as 174,125.224.80 (yes with typo).

I did notice that ipv6 was not disabled so I have now disabled it.  this is what I now get with the nslookup google.com

listening on any, link-type LINUX_SLL (Linux cooked), capture size 1600 bytes
10:27:47.437951 IP 127.0.0.1.55670 > 127.0.0.1.53: 40491+ A? google.com. (28)
10:27:53.438079 IP 127.0.0.1.55670 > 127.0.0.1.53: 40491+ A? google.com. (28)
10:27:59.438384 IP 127.0.0.1.55670 > 127.0.0.1.53: 40491+ A? google.com. (28)

---

### Post by jonobr on 2011-12-23
Thanks

That clears it up.

The problem however still appears to be that your resolution is going to 127.0.0.1 not the dns server.

I would recommend modifying your /etc/resolv.conf file and add in the dns entry manually.

If you go to a working machine and cat /etc/resolv.conf it wsill show the correct address that should be in there.

If that works then thats ok, but if you are using nm applet it will overwrite the file on the reboot.

The problem really though is why you are using 127.0.0.1
Did you configure that in nm applet for dns?

If its in resolv.conf thats good, we know where it is, replace it with the working one.

If it works, reboot and see if its overwritten

cheers

---

### Post by JohnsonMR on 2011-12-23
> **jonobr said:**
> Thanks

That clears it up.

The problem however still appears to be that your resolution is going to 127.0.0.1 not the dns server.

I would recommend modifying your /etc/resolv.conf file and add in the dns entry manually.

If you go to a working machine and cat /etc/resolv.conf it wsill show the correct address that should be in there.

If that works then thats ok, but if you are using nm applet it will overwrite the file on the reboot.

The problem really though is why you are using 127.0.0.1
Did you configure that in nm applet for dns?

If its in resolv.conf thats good, we know where it is, replace it with the working one.

If it works, reboot and see if its overwritten

cheers


As you expected the /etc/resolv.conf was blank.  So I manually entered the correct information, rebooted, and it was blank again.  I then entered the information again, remove NetworkManager (as many before me have done), rebooted and everything is good.

If removing NetworkManager was not the correct thing to do, then let me know what I should have done.  In any case, it's working so far.

Thank you very much...

---

### Post by jonobr on 2011-12-23
so , i never use nm as i have had too much trouble in the past with it.

The thing to remember is if you configure files yourself then you cant use nm applet and vice versa.

Dns should have been supplied by dhcp but i guess dns in nm may have been checked but empty

Therefore it kept overwriting with nothing.

If your comfortable using files , i would stick with that


one additional thing 
 surprised pinging by ip earlier didnt work&#8230;

---

### Post by JohnsonMR on 2011-12-23
This may be just a bandaid as nm is running fine on my other pc's.  This is the only one that has a static ip adr as it's a print/file share server.  I don't think it's been rebooted for 6 months (wish I could do that with my win boxes).   It just started failing when I decided it needed some updates.   One of the cold/snowy days I'll sit down and find out why.  But for now it just works and that's good enough for me.

---

