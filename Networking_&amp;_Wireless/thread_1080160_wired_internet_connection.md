---
title: "wired internet connection"
date: 2009-02-25
forum: Networking &amp; Wireless
---

### Post by pfiorentino on 2009-02-25
Hi,
I'm a newby of UBUNTU. I have just installed ubuntu 8.10 on my notebook ibm A31, but I have some problems with internet connection (with cable). 
I have a router digicom and two PC with windows connected with also. 
I setup all parameters on notebook and I can ping the router, but I can't ping two other PCs and I can't ping others ip outside my local network, but I can ping from other PC to my notebook. I can't connect to internet from my notebook of course even if I setup dns server correctly. 
I can type only [http://192.168.1.254](http://192.168.1.254) (my router) in the browser of notebook and I can see the parameters of my router, but they look good.   
Help me, please.
Paolo Fiorentino

---

### Post by x33a on 2009-02-25
post the output of
```
ifconfig
cat /etc/network/interfaces
```
from a terminal

---

### Post by pfiorentino on 2009-02-25
ifconfig:

eth0
Link encap:Ethernet HWaddr 00:02:8a:a5:57:ba
inet addr:192.168.1.7 Bcast:192.168.1.255 Mask:255.255.255.0
inet6 addr: fe80::202:8aff:fea5:57ba/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:3502 errors:0 dropped:0 overruns:0 frame:0 
TX packets:1239 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:373447 (373.4 KB) TX bytes 243565 (243.5 KB) 

lo
Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.255.255.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:243 errors:0 dropped:0 overruns:0 frame:0 
TX packets:243 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:15708 (15.7 KB) TX bytes 15708 (15.7 KB) 

cat /etc/network/interfaces
auto lo
iface lo inet loopback

thanks

---

### Post by superprash2003 on 2009-02-25
in your terminal type **sudo iptables -L** ... do you run firestarter or anything similar? also type **ping google.com** and post output.. also try opening [http://74.125.67.100](http://74.125.67.100)

---

### Post by x33a on 2009-02-26
you'll have to set the connection (if you are not using the router in-built dialer).

try
```
sudo pppoeconf
```

---

### Post by pfiorentino on 2009-03-14
ok, I reinstalled ubuntu 8.10 on my notebook and it works very well with cable. According to me there were some problems with disk of my computer. I reformatted and reinstalled and I resolved my problems. Now I want configure my pen usb wireless with chipset RTL 8187B, but I open a new topic.

Thank you

---

