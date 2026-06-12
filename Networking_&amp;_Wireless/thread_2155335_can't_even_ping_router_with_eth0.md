---
title: "can't even ping router with eth0"
date: 2013-06-17
forum: Networking &amp; Wireless
---

### Post by strattonbrazil on 2013-06-17
My internet on my 64-bit 12.10 install suddenly stopped working.  Looking at ifconfig, I see I have a valid IP address (192.168.0.7) from dhcp.  However, I can't seem to reach anything else.  I can ping localhost or my interface's IP, but not the internet or even the router at 192.168.0.1.  Actually, what seems weird is I do get one ping response from the router, but it takes a while.  

I've tried disabling IPv6 in /etc/sysctl.conf and commenting out dns=/etc/NetworkManager/NetworkManager.conf, but that doesn't seem to affect the ping.  My resolve.conf points to 127.0.0.1, which may or may not be an issue.  I've tried removing it without a noticeable change.  I've tried playing with the routing tables, but I think I may have screwed them up.  If it might be a routing table issue, is there a program that normally configure that?  Should I blow the lines away and try adding some line for my setup?  

It all seems very confusing that it just stopped working in the middle of a show and won't work anymore.  Even weirder that I only seem to get one ping back.

---

### Post by papibe on 2013-06-18
Hi  strattonbrazil.

Could you post the results of these commands?
```
ifconfig

cat /etc/resolv.conf 

ls -l /etc/resolv.conf

grep dns /etc/NetworkManager/NetworkManager.conf 

cat /var/run/nm-dns-dnsmasq.conf

nslookup ubuntu.com

dig ubuntuforums.org

route -n
```
Regards.

---

### Post by strattonbrazil on 2013-06-18
**ifconfig**
[FONT=Courier New]
eth0      Link encap:Ethernet  HWaddr 00:24:1d:2a:8f:f7  
          inet addr:192.168.0.6  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:503 errors:0 dropped:0 overruns:0 frame:0
          TX packets:975 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:56798 (56.7 KB)  TX bytes:89027 (89.0 KB)

eth1      Link encap:Ethernet  HWaddr 00:1f:d0:81:a2:ef  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:940 errors:0 dropped:0 overruns:0 frame:0
          TX packets:940 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:75216 (75.2 KB)  TX bytes:75216 (75.2 KB)
[/FONT]

**cat /etc/resolv.conf**
File doesn't exist...

**ls -l /etc/resolv.conf**
Broken link

**grep dns /etc/NetworkManager/NetworkManager.conf**
[FONT=Courier New]
#dns=dsnmasq
[/FONT]

**cat /var/run/nm-dns-dnsmasq.conf**
File doesn't exist...

**nslookup ubuntu.com**
[FONT=Courier New]
;; connection timed out; no servers could be reached
[/FONT]


**dig ubuntuforums.org**
[FONT=Courier New]
; <<>> DiG 9.8.1-P1 <<>> ubuntuforums.org
;; global options: +cmd
;; connection timed out; no servers could be reached
[/FONT]

**route -n**
[FONT=Courier New]
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
192.168.0.0     192.168.0.1     255.255.255.0   UG    0      0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
[/FONT]

---

### Post by papibe on 2013-06-18
Thanks.

You need to have a /etc/resolv.conf file in order to resolve Internet addresses.

In 12.10 that file is created dynamically by the network stack and it is a symbolic link to  /run/resolvconf/resolv.conf 

Try reconfiguring the resolver package by running this:
```
sudo dpkg-reconfigure resolvconf
```
Check if the  link was recreated:
```
ls -l /etc/resolv.conf 
lrwxrwxrwx 1 root root 29 Dec 23 18:50 /etc/resolv.conf -> ../run/resolvconf/resolv.conf

```
If that didn't do it, you can manually recreate the file:
```
sudo ln -s  /run/resolvconf/resolv.conf /etc/resolv.conf
```
Then restart your network:
```
sudo service networking restart
```
That should do it. 

Let us know if that helps.
Regards.

---

