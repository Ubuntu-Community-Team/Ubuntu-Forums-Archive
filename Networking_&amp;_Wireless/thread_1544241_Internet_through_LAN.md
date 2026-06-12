---
title: "Internet through LAN"
date: 2010-08-02
forum: Networking &amp; Wireless
---

### Post by uttamsen on 2010-08-02
Hi,

 I am new to Ubuntu environment. I use LAN as my internet connection. I have set all proxy settings requires for the network as well as that in Firefox. (The setup woks with the Windows XP in the same PC). But in  ubuntu it is not working. It shows network to be connected but no internet access.

Any idea please?

with regards,
Uttam

---

### Post by wbrokow1 on 2010-08-02
Same problem here. 10.04 frsh install. No Internet, but LAN works . Nobody's solution has worked for me yet.

Any help out there?
Thanks,

---

### Post by ahbart on 2010-08-02
Did your pc get an ip address? 
Have a look at network manager and search for info.
Or type ifconfig in a terminal.

---

### Post by dineshs on 2010-08-02
can you post the results of
```
route -n
```

---

### Post by Aragwain on 2010-08-02
Check if you have a nice IP address and check gateway.

You could post them here. ;)

---

### Post by wbrokow1 on 2010-08-02
route -n

gives headings but nothing in the table.

---

### Post by dineshs on 2010-08-03
Can you post the output of
```
route print
```[COLOR="Blue"]in windows [/COLOR]and ```
ifconfig -a
``` in [COLOR="Blue"]ubuntu[/COLOR]

---

### Post by uttamsen on 2010-08-09
In ubuntu **iconfig -a** gives:

eth0      Link encap:Ethernet  HWaddr 00:27:0e:0c:88:72  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:27 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:76 errors:0 dropped:0 overruns:0 frame:0
          TX packets:76 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5648 (5.6 KB)  TX bytes:5648 (5.6 KB)


The output in windows is given as attachment
 
**route -n** gives only heading, nothing else

---

### Post by dineshs on 2010-08-09
Are you using 10.04 ?Have you tried setting IP manually via Network manager?

---

### Post by uttamsen on 2010-08-09
Yah, it is 10.04.

I have already set the IP in everywhere possible

---

### Post by dineshs on 2010-08-09
please run```
sudo dhclient eth0
```and see if route -n shows IP and gateway.If not try this
[http://ubuntuforums.org/showpost.php?p=9693408&postcount=3](http://ubuntuforums.org/showpost.php?p=9693408&postcount=3)
[COLOR="Blue"]but [/COLOR]give IP 10.110.200.8
mask 255.255.0.0
gateway 10.110.250.1

---

### Post by uttamsen on 2010-08-09
after entering route - n it gives
kernel IP routing table
destination   gateway   genmask      flags    matric   ref  use Iface
169.254.0.0 0.0.0.0     255.255.0.0   U         1000      0   0 etho
10.110.0.0   0.0.0.0     255.255.0.0   U         0           0   0 etho

now what will do?

---

### Post by dineshs on 2010-08-09
No gateway still?
Did you hit enter key after giving IP, mask and gateway (before giving DNS)please check.And after giving DNS apply

---

