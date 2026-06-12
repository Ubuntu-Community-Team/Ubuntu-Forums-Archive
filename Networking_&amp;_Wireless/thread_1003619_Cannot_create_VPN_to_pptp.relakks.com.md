---
title: "Cannot create VPN to pptp.relakks.com"
date: 2008-12-06
forum: Networking &amp; Wireless
---

### Post by Martin B on 2008-12-06
Hi,

I have used this guide [http://suprbay.org/showthread.php?t=12923](http://suprbay.org/showthread.php?t=12923) to setup a VPN connection to Relakks, a Swedish anonymizer.

I run an Ubuntu 8.10 LAMP server.

When I try to connect to Relakks I get the folowing:

root@Server:~# pon relakks
Using interface ppp0
Connect: ppp0 <--> /dev/pts/1
LCP: timeout sending Config-Requests
Connection terminated.
Modem hangup
root@Server:~# 

When I run "route -n" to check my routing table it looks like it maps the correct IP addresses. However I expected to see a line for "PPP0", as in the guide above, it's not there though...

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
83.233.181.2    192.168.1.1     255.255.255.255 UGH   0      0        0 eth0
83.233.183.2    192.168.1.1     255.255.255.255 UGH   0      0        0 eth0
83.233.169.2    192.168.1.1     255.255.255.255 UGH   0      0        0 eth0
83.233.180.2    192.168.1.1     255.255.255.255 UGH   0      0        0 eth0
83.233.182.2    192.168.1.1     255.255.255.255 UGH   0      0        0 eth0
83.233.168.2    192.168.1.1     255.255.255.255 UGH   0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 eth0

As I said, I have followed the instructions above to the letter, but no good...

Grateful for advise on how to get this to work.

//Martin

---

### Post by Daggoo on 2008-12-30
Bump.

I'm having the exact same problem with 8.10 Desktop.

Thanks,

Andreas

---

### Post by fathhi001 on 2009-03-01
hi there while im seekin de ubuntu forum website, accidently found your threads,im trying to make mdsl sudani works with unbuntu, ive been struggling  for two weeks but still cant, its freaken complicated,i reconfiged the wvdial text as uve described,even though when i try to access as a root, i get the same problem. so I accessed the internet via windows,because there is no connetion with ubuntu and downloaded the gppp dial up, according to rules  wvdial doesn't work and it runs as a command line, thus the gppp won't even work because its the same functions comparing with wvdial but it runs graphically.I did call the main help center of ZTE and i got their helps,they have sent me this program "zteac8700forlinuxsystem" but still have some problems to open it , it says the archive can't access the files. by the way my ubuntu is installed inside windows as a dual boot.  

ubuntu 8.04 hardy.         

any help and ill be appreciated

---

