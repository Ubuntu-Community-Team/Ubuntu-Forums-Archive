---
title: "DNS look-up failed after upgrade"
date: 2012-11-12
forum: Networking &amp; Wireless
---

### Post by sqrooup on 2012-11-12
Have recently upgraded my laptop from 12.04 to 12.10. Now when I go online websites "can't be found because the DNS look-up failed." 
Laptop is dual boot with Windows 7, which works fine.
Have tried wired and wireless, but to no avail.
Have looked at other messages, and result of;
```
ping -c3 www.google.com
ping: unknown host www.google.com
```
I can not find a method of setting DNS automatically!

---

### Post by papibe on 2012-11-12
Hi sqrooup.

Could you post the result of these commands?
```
ifconfig

route -n

cat /etc/resolv.conf

grep dnsmasq /etc/NetworkManager/NetworkManager.conf

cat /var/run/nm-dns-dnsmasq.conf
```
Regards.

---

### Post by sqrooup on 2012-11-12
ifconfig
```
eth0      Link encap:Ethernet  HWaddr 00:03:0d:ef:c3:cf  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::203:dff:feef:c3cf/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:114 errors:0 dropped:0 overruns:0 frame:0
          TX packets:187 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:30884 (30.8 KB)  TX bytes:38495 (38.4 KB)
          

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:7305 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7305 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:562344 (562.3 KB)  TX bytes:562344 (562.3 KB)

wlan0     Link encap:Ethernet  HWaddr 40:61:86:40:45:a6  
          inet6 addr: fe80::4261:86ff:fe40:45a6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10 errors:0 dropped:1900 overruns:0 frame:0
          TX packets:813 errors:5 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3244 (3.2 KB)  TX bytes:71666 (71.6 KB)
          Interrupt:17 Memory:f8c38000-f8c38100

```note: wireless disconected
route -n
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

```
cat /etc/resolv.conf
```
cat: /etc/resolv.conf: No such file or directory
```
grep dnsmasq /etc/NetworkManager/NetworkManager.conf
```
grep: /etc/NetworkManager/NetworkManager.conf: No such file or directory
```
cat /var/run/nm-dns-dnsmasq.conf
```
cat: /var/run/nm-dns-dnsmasq.conf: No such file or directory
```

Seem to have many files missing

---

### Post by papibe on 2012-11-12
Thanks.

Indeed. There seems to be a bigger problem.

First, let's do a quick fix for your current session and add a valid nameserver.

If your router provides DNS, do this:
```
sudo bash -c 'echo "nameserver 192.168.1.254" > /etc/resolv.conf'
```
If not, do this:
```
sudo bash -c 'echo "nameserver 8.8.8.8" > /etc/resolv.conf'
```
You should be able to ping and access the Internet now.

Let us know how that goes, so we can tackle why your are missing those files.
Regards.

---

### Post by sqrooup on 2012-11-13
Still nothing, ping still shows;
```
ping -c3 www.google.com
ping: unknown host www.google.com
```

---

### Post by papibe on 2012-11-13
Sorry to hear that.

Did you use the router or Google's public DNS (8.8.8.8 )?

Could you post the result of these commands?
```
cat /etc/nsswitch.conf

nslookup ubuntu.com

dig google.com
```
Regards.

---

### Post by sqrooup on 2012-11-13
Google was just an example from a previous tread, used router, both in 8.8.8.8 and 192.168.1.254

cat /etc/nsswitch.conf
```
# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc-reference' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

passwd:         compat
group:          compat
shadow:         compat

hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis

```
nslookup ubuntu.com
```
;; connection timed out; no servers could be reached
```
dig google.com
```
; <<>> DiG 9.8.1-P1 <<>> google.com
;; glogal options: +cmd
;; connection timed out; no servers could be reached
```

Note: have a spare 12.04 disc and have backed up all my files; is it possible to back up all my Chrome bookmarks (just in case)?

---

### Post by papibe on 2012-11-13
:-k puzzling...

Could you access your admin router page?

Could you check that the router's network settings are indeed 192.68.1.*?

Could you post the result of these commands?
```
tracepath 192.168.1.254

tracepath google.com
```
Regards.

---

### Post by sqrooup on 2012-11-14
I am running a Xubuntu desktop on same network, it's address is 192.168.1.1, and it connects ok.
And no problems getting into admin router page.

192.168.1.254
```
1:  paul-lappy.local                                    0.101ms pmtu 1500
 1:  192.168.1.254                                         1.676ms reached
 1:  192.168.1.254                                         1.389ms reached
     Resume: pmtu 1500 hops 1 back 255 

```
google.com
```
gethostbyname2: unknown host
```

---

