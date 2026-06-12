---
title: "How to Connect Ubuntu Desktop and Windows XP Laptop"
date: 2009-12-19
forum: Networking &amp; Wireless
---

### Post by echoforever on 2009-12-19
Hi,

I have installed Ubuntu 9.04 on my desktop. I connect to the internet using an ADSL modem/router ([http://www.semindia.in/SemIndiaSystems_products_A211_TS.html](http://www.semindia.in/SemIndiaSystems_products_A211_TS.html))

I have configured eth0 to use dynamic IP as I can't get it working with a static IP

```
/etc/network/interfaces file:

auto eth0
iface eth0 inet manual
#iface eth0 inet static
#address 192.168.1.2
#netmask 255.255.255.0
#gateway 192.168.1.1
#broadcast 192.168.1.255
pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf

auto dsl-provider
iface dsl-provider inet ppp
provider dsl-provider

```

I am able to configure the network connection on my laptop to use a fixed IP 192.168.1.4 and gw address.

Can anyone help me connect these two systems to the LAN.

regards.

---

### Post by Jaiibee on 2009-12-19
1. apt-get install samba
2. Go to Places -> Network
3. Go to Windows Network

Then you just need to log into the machine. That's how it worked for me, at least.

---

### Post by echoforever on 2009-12-20
Hi Jaiibee,
Thanks for helping.

Installing samba did not work.
I get this error:
```
Unable to mount location
Failed to retrieve share list from server
```
I couldn't find any solution for this error either.

I guess the absence of UG flag is related to this problem.

```
$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
117.195.192.1   0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
0.0.0.0         0.0.0.0         0.0.0.0         U     0      0        0 ppp0
```

```
$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:e0:20:71:4e:c7  
          inet6 addr: fe80::2e0:20ff:fe71:4ec7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6765 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6977 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3607598 (3.6 MB)  TX bytes:1257967 (1.2 MB)
          Interrupt:22 Memory:ff8ffc00-ff8ffcff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:92 errors:0 dropped:0 overruns:0 frame:0
          TX packets:92 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4224 (4.2 KB)  TX bytes:4224 (4.2 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:117.195.193.37  P-t-P:117.195.192.1  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1460  Metric:1
          RX packets:6524 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6731 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:3448876 (3.4 MB)  TX bytes:1094957 (1.0 MB)
```

regards.

---

### Post by echoforever on 2009-12-20
Got it working. I have activated static IP for eth0, but I left gateway entry commented in /etc/network/interfaces file.

```
auto eth0
#iface eth0 inet manual
iface eth0 inet static
address 192.168.1.2
netmask 255.255.255.0
#gateway 192.168.1.1
#broadcast 192.168.1.255
```

Unblocked DCOM-scm and Samba (SMB)services in firewall.
Created a Samba user to access the shared files.
```
sudo smbpasswd -L -a <user name>
```

I can now access Ubuntu Desktop from Run command in Windows and I can acces windows box using rdesktop from Ubuntu. :KS

---

