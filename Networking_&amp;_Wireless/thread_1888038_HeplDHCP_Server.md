---
title: "Hepl:DHCP Server"
date: 2011-11-28
forum: Networking &amp; Wireless
---

### Post by Linux99 on 2011-11-28
Hi..

I can't install dhcp server on ubuntu using terminal.Then, I install Gadmin-dhcpd 0.4.9 using ubuntu software center but it shows error message : [COLOR=Red]ISC dhcpd is not installed or not in your path.[/COLOR]Plz, help me... thanks in advance.

---

### Post by jonobr on 2011-11-28
What happens when you 
```
sudo apt-get install dhcp3-server
```
Do you see any errors?

Or are you using ISC for DHCP?

---

### Post by Linux99 on 2011-11-29
> **jonobr said:**
> What happens when you 
```
sudo apt-get install dhcp3-server
```Do you see any errors?

Or are you using ISC for DHCP?

Hi jonobr..
I reinstall ubuntu again!!
First, I add new network card "eth1'" (vmware)
assigned static ip 192.168.1.65 subnet mask 255.255.255.192
then i install dhcp server using ```
sudo apt-get install dhcp3-server
``` and the final log was:
```

Selecting previously deselected package dhcp3-server.
Unpacking dhcp3-server (from .../dhcp3-server_4.1.1-P1-15ubuntu9.1_all.deb) ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
Setting up isc-dhcp-server (4.1.1-P1-15ubuntu9.1) ...
 * Starting ISC DHCP server dhcpd                                             
   * check syslog for diagnostics.
                                                                        [COLOR=Red] [fail][/COLOR]

```then i modified config file in  /etc/dhcp3/dhcpd.conf (also i find an other one in /etc/dhcp) :

```

ddns-update-style none;
default-lease-time 600;
max-lease-time 7200;

subnet 192.168.1.64 netmask 255.255.255.192 {
  interface eth1;
  range 192.168.1.77 192.168.1.126;
  option subnet-mask 255.255.255.192;
  option broadcast-address 192.168.1.127;
  option routers 192.168.88.1;
option ip-forwarding off;
option ntp-servers 192.168.1.65;
}

``` then i try to start dhcp but give me this message:

```
s@ubuntu:/$ sudo service  dhcp3-server start
dhcp3-server: unrecognized service

```

---

### Post by jonobr on 2011-11-29
Anything of interest in the syslog

```
cat /var/log/syslog | grep dhcp 
```

and if you do 

```
sudo /etc/init.d/dhcp3d status
```
does it show anything of interest
(or the similar command for isc

Does you Ifocnfig show the eth1 is ok?

---

### Post by Linux99 on 2011-11-29
> **jonobr said:**
> Anything of interest in the syslog

```
cat /var/log/syslog | grep dhcp 
```and if you do 

give me this:
```

Nov 29 16:02:33 ubuntu dhcpd: Internet Systems Consortium DHCP Server 4.1.1-P1
Nov 29 16:02:33 ubuntu dhcpd: Copyright 2004-2010 Internet Systems Consortium.
Nov 29 16:02:33 ubuntu dhcpd: All rights reserved.
Nov 29 16:02:33 ubuntu dhcpd: For info, please visit https://www.isc.org/software/dhcp/
Nov 29 16:02:33 ubuntu dhcpd: Wrote 0 leases to leases file.
Nov 29 16:02:33 ubuntu dhcpd: 
Nov 29 16:02:33 ubuntu dhcpd: No subnet declaration for eth1 (192.168.1.65).
Nov 29 16:02:33 ubuntu dhcpd: ** Ignoring requests on eth1.  If this is not what
Nov 29 16:02:33 ubuntu dhcpd:    you want, please write a subnet declaration
Nov 29 16:02:33 ubuntu dhcpd:    in your dhcpd.conf file for the network segment
Nov 29 16:02:33 ubuntu dhcpd:    to which interface eth1 is attached. **
Nov 29 16:02:33 ubuntu dhcpd: 
Nov 29 16:02:33 ubuntu dhcpd: 
Nov 29 16:02:33 ubuntu dhcpd: Not configured to listen on any interfaces!


```

```
sudo /etc/init.d/dhcp3d status
```does it show anything of interest
(or the similar command for isc
```

s@ubuntu:/$ sudo /etc/init.d/dhcpd status
sudo: /etc/init.d/dhcpd: command not found
s@ubuntu:/$ sudo /etc/init.d/dhcp3 status
sudo: /etc/init.d/dhcp3: command not found
s@ubuntu:/$ sudo /etc/init.d/dhcp3-server status
sudo: /etc/init.d/dhcp3-server: command not found


```

Does you Ifocnfig show the eth1 is ok?
```

eth0      Link encap:Ethernet  HWaddr 00:0c:29:59:0e:ed  
          inet addr:192.168.95.139  Bcast:192.168.95.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:29ff:fe59:eed/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7799 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6734 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8189433 (8.1 MB)  TX bytes:832816 (832.8 KB)
          Interrupt:19 Base address:0x2000 

eth1      Link encap:Ethernet  HWaddr 00:0c:29:59:0e:f7  
          inet addr:192.168.1.65  Bcast:192.168.1.127  Mask:255.255.255.192
          inet6 addr: fe80::20c:29ff:fe59:ef7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:65 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:16159 (16.1 KB)
          Interrupt:19 Base address:0x2080 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:420 errors:0 dropped:0 overruns:0 frame:0
          TX packets:420 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:33816 (33.8 KB)  TX bytes:33816 (33.8 KB)


```

---

### Post by jonobr on 2011-11-29
Your getting a standard error message when there is a problem with the declaration in dhcpd.conf
As a result it cant process the configuration file and wont start the service.

Looking again at your dhcpd.conf

Im thinking you need to change the line

```
subnet-mask 255.255.255.192
```

to


```
netmask 255.255.255.192
```

---

