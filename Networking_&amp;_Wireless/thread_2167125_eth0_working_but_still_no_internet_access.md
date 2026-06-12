---
title: "eth0 working but still no internet access"
date: 2013-08-12
forum: Networking &amp; Wireless
---

### Post by sergio3 on 2013-08-12
Hi,

I have a server running Ubuntu 12.04. I set it up originally with a static ip and now switched back to dynamic trying to fix my problem. I can't access the internet, yet I ping with 100% successful packet transfer. I really have no idea what is going on but here is some stuff that could be useful stuff:



ifconfig:


eth0      Link encap:Ethernet  HWaddr 00:12:3f:6e:f7:7d  
          inet addr:18.250.6.14  Bcast:18.250.255.255  Mask:255.255.0.0
          inet6 addr: fe80::212:3fff:fe6e:f77d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4402 errors:0 dropped:0 overruns:0 frame:0
          TX packets:247 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:423413 (423.4 KB)  TX bytes:30412 (30.4 KB)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


route:


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         W92-RTR-1-W1.MI 0.0.0.0         UG    100    0        0 eth0
18.250.0.0      *               255.255.0.0     U     0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0


my /etc/network/interfaces:


auto lo
iface lo inet loopback
auto eth0
iface eth0 inet dhcp


my nameservers:


nameserver 18.71.0.151
nameserver 18.70.0.160
nameserver 18.72.0.3
search mit.edu


ifconfig -a | grep eth0 :
eth0      Link encap:Ethernet  HWaddr 00:12:3f:6e:f7:7d 


Any help is appreciated. I ran out of ideas.

-Sergio

---

### Post by papibe on 2013-08-12
Hi sergio3.

Did you restart your network after the changes? If not, do this:
```
sudo service networking restart
```

If that doesn't help, could you post the results of these commands?
```
route -n

nslookup ubuntu.com

dig ubuntuforums.org

mtr -rnc 1 W92-RTR-1-W1.MI

mtr -rnc 1 8.8.8.8
```
Regards.

---

### Post by sergio3 on 2013-08-12
Thanks for your response. I restarted networking using /etc/init.d/networking restart because service networking restart threw an error (pasted below). I ran the other commands and here are the outputs:

ifconfig:


eth0      Link encap:Ethernet  HWaddr 00:12:3f:6e:f7:7d  
          inet addr:18.250.6.14  Bcast:18.250.255.255  Mask:255.255.0.0
          inet6 addr: fe80::212:3fff:fe6e:f77d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4402 errors:0 dropped:0 overruns:0 frame:0
          TX packets:247 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:423413 (423.4 KB)  TX bytes:30412 (30.4 KB)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


route:


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         W92-RTR-1-W1.MI 0.0.0.0         UG    100    0        0 eth0
18.250.0.0      *               255.255.0.0     U     0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0


my /etc/network/interfaces:


auto lo
iface lo inet loopback
auto eth0
iface eth0 inet dhcp


my nameservers:


nameserver 18.71.0.151
nameserver 18.70.0.160
nameserver 18.72.0.3
search mit.edu


ifconfig -a | grep eth0 :
eth0      Link encap:Ethernet  HWaddr 00:12:3f:6e:f7:7d

---

### Post by sergio3 on 2013-08-12
Oopse. These are the outputs. I forgot to copy.:

service networking restart:
stop: Unknown instance: 
networking stop/waiting




route -n:
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         18.250.0.1      0.0.0.0         UG    100    0        0 eth0
18.250.0.0      0.0.0.0         255.255.0.0     U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0




nslookup ubuntu.com:
Server:		18.71.0.151
Address:	18.71.0.151#53


Non-authoritative answer:
Name:	ubuntu.com
Address: 91.189.94.156




dig ubuntuforums.org:


; <<>> DiG 9.8.1-P1 <<>> ubuntuforums.org
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 61679
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 3, ADDITIONAL: 0


;; QUESTION SECTION:
;ubuntuforums.org.		IN	A


;; ANSWER SECTION:
ubuntuforums.org.	286	IN	A	91.189.94.12


;; AUTHORITY SECTION:
ubuntuforums.org.	164971	IN	NS	ns1.canonical.com.
ubuntuforums.org.	164971	IN	NS	ns3.canonical.com.
ubuntuforums.org.	164971	IN	NS	ns2.canonical.com.


;; Query time: 0 msec
;; SERVER: 18.71.0.151#53(18.71.0.151)
;; WHEN: Mon Aug 12 13:51:08 2013
;; MSG SIZE  rcvd: 117




mtr -rnc 1 W92-RTR-1-W1.MI:
Failed to resolve host: Name or service not known
root@Sergio-Server:~# 




mtr -rnc 1 8.8.8.8:
HOST: Sergio-Server               Loss%   Snt   Last   Avg  Best  Wrst StDev
  1.|-- 18.250.0.1                 0.0%     1    0.4   0.4   0.4   0.4   0.0
  2.|-- 18.168.1.1                 0.0%     1    0.4   0.4   0.4   0.4   0.0
  3.|-- 18.168.5.2                 0.0%     1    0.7   0.7   0.7   0.7   0.0
  4.|-- 18.192.7.2                 0.0%     1    0.6   0.6   0.6   0.6   0.0
  5.|-- 198.32.238.22              0.0%     1    5.5   5.5   5.5   5.5   0.0
  6.|-- 72.14.239.248              0.0%     1    5.7   5.7   5.7   5.7   0.0
  7.|-- 72.14.236.206              0.0%     1    5.8   5.8   5.8   5.8   0.0
  8.|-- 209.85.249.11              0.0%     1   12.3  12.3  12.3  12.3   0.0
  9.|-- 66.249.95.229              0.0%     1   20.0  20.0  20.0  20.0   0.0
 10.|-- 72.14.234.55               0.0%     1   21.0  21.0  21.0  21.0   0.0
 11.|-- ???                       100.0     1    0.0   0.0   0.0   0.0   0.0
 12.|-- 8.8.8.8                    0.0%     1   20.1  20.1  20.1  20.1   0.0

---

### Post by papibe on 2013-08-12
Thanks.

Try this:
```
sudo service networking start
```
Regards.

---

### Post by sergio3 on 2013-08-12
I did it but still not working.

Actually, it wasn't an error. It just said "networking stop/waiting".

---

### Post by papibe on 2013-08-12
OK.

It looks like you are able to both resolve names and access external sites (8.8.8.8 is Google Public DNS).

Why do you say you don't have Internet access? Could you gives a little more details?

Regards

---

### Post by sergio3 on 2013-08-12
Oh wow. It works now. Even though the network manager still doesn't detect a connection. Originally I couldn't load pages either.

---

### Post by Hadaka on 2013-08-12
Hi, give this a try..
```
sudo gedit /etc/network/interfaces
```
comment out your last 2 lines and make it look like this..
```
auto lo
iface lo inet loopback
```
Save and close gedit.
then do..
```
sudo service network-manager restart
```
you may also want to configure your network mgr connection to look like the attached.
[ATTACH=CONFIG]245322[/ATTACH]
boot and you should be good.
thanks

---

### Post by sergio3 on 2013-08-12
That got the network manager working! Thank you both for your help, I'm rather new to linux in general as you may have noticed :)

---

### Post by papibe on 2013-08-12
@Hadaka: You brought up something worth mentioning.

On post #1, sergio3 mentions that it is a server. Under that assumption, i.e., a truly install of Ubuntu Server Edition, sergio3's syntax of '/etc/network/interfaces' is correct, and the command to start/stop the network is what I described in my previous posts.

However, in the case this is a Desktop Edition working as a "server" (network-manager installed), then by all means Hadaka's instruction are the ones to follow.

@sergio3:

You can know if network-manager is installed by running:
```
apt-cache policy network-manager
```

Regards.

---

