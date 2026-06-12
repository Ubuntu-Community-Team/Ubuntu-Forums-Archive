---
title: "DSL connection Error"
date: 2010-05-15
forum: Networking &amp; Wireless
---

### Post by Fibero on 2010-05-15
Hi guys..
I'm new here..I faced a problem with my DSL connection in Ubuntu 10.04.
Once I type this 

       " sudo pon dsl-provider " 

it's showing me an error

" Plugin rp-pppoe.so loaded.
RP-PPPoE plugin version 3.8p compiled against pppd 2.4.5"

And I could not connect to internet.
Anyone have an idea to fix this?

Thanks in advance.
Fibero

---

### Post by karthick87 on 2010-05-15
Can you ping the connection?

---

### Post by dineshs on 2010-05-15
You are using Bridge mode which requires a PPPoE connection to be created in the OS.But most modems can be configured with username and password(Called Modem in PPPoE mode).Why dont you try that? Pl post the output of
```
ifconfig -a
```
What is the model name of yr modem?

---

### Post by Fibero on 2010-05-15
> **dineshs said:**
> You are using Bridge mode which requires a PPPoE connection to be created in the OS.But most modems can be configured with username and password(Called Modem in PPPoE mode).Why dont you try that? Pl post the output of
```
ifconfig -a
```What is the model name of yr modem?

Oke. I'll try that. But I must switch to the Ubuntu OS. Coz now I'm using another OS.
My modem is ADSL SA 5100.

---

### Post by dineshs on 2010-05-15
It is possible to configure your modem in PPPoe mode I think.If you do so you need not use pppconfig/pon dsl-provider and can directly use your web browser to access internet whichever be your OS.
[http://syamsyah.wordpress.com/2008/11/08/panduan-konfigurasi-modem-adsl-speedy-sanex-sa-5100/](http://syamsyah.wordpress.com/2008/11/08/panduan-konfigurasi-modem-adsl-speedy-sanex-sa-5100/)
But you must know your username, password,VPI, VCI etc.from your ISP.
Forgot to ask.Is it connected via ethernet

---

### Post by Fibero on 2010-05-15
> **dineshs said:**
> It is possible to configure your modem in PPPoe mode I think.If you do so you need not use pppconfig/pon dsl-provider and can directly use your web browser to access internet whichever be your OS.
[http://syamsyah.wordpress.com/2008/11/08/panduan-konfigurasi-modem-adsl-speedy-sanex-sa-5100/](http://syamsyah.wordpress.com/2008/11/08/panduan-konfigurasi-modem-adsl-speedy-sanex-sa-5100/)
But you must know your username, password,VPI, VCI etc.from your ISP.
Forgot to ask.Is it connected via ethernet

Hi dineshs I tried your methode by typing
 " ifconfig -a " 
and showing this 
eth0      Link encap:Ethernet  HWaddr 00:1e:68:10:ac:df  
          inet6 addr: fe80::21e:68ff:fe10:acdf/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:207 errors:0 dropped:0 overruns:0 frame:0
          TX packets:191 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:12598 (12.5 KB)  TX bytes:8251 (8.2 KB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:221498 errors:0 dropped:0 overruns:0 frame:0
          TX packets:221498 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:19128780 (19.1 MB)  TX bytes:19128780 (19.1 MB)

wlan0     Link encap:Ethernet  HWaddr 00:17:c4:17:fe:00  
          inet6 addr: fe80::217:c4ff:fe17:fe00/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:56 (56.0 B)  TX bytes:2016 (2.0 KB)

But I'm still no luck
And for your link, my GUI modem it's totally different now. Probably the GUI change by the provider.
Any another solution?

---

### Post by dineshs on 2010-05-15
> Forgot to ask.Is it connected via ethernet 
I hope your modem is connected via ethernet and is not a DHCP enabled one.if so pl try to configure IP manually..For this
Right-click on the nm-applet and then click on Edit Connections. 
Select the tab, wired 
select the ethernet connection and click edit(you can add the ethernet connection if not listed) 
select ipv4 
method-manual 
click add 
address 192.168.1.100 
mask 255.255.255.0 
gateway 192.168.1.1 
then hit enter 
DNS 8.8.8.8 
then click apply 
ref:[https://help.ubuntu.com/community/NetworkManager0.7](https://help.ubuntu.com/community/NetworkManager0.7) 
After doing this restart your machine and post the output of
```
ping -c5 192.168.1.1
```

---

### Post by Fibero on 2010-05-15
> **dineshs said:**
> I hope your modem is connected via ethernet and is not a DHCP enabled one.if so pl try to configure IP manually..For this
Right-click on the nm-applet and then click on Edit Connections. 
Select the tab, wired 
select the ethernet connection and click edit(you can add the ethernet connection if not listed) 
select ipv4 
method-manual 
click add 
address 192.168.1.100 
mask 255.255.255.0 
gateway 192.168.1.1 
then hit enter 
DNS 8.8.8.8 
then click apply 
ref:[https://help.ubuntu.com/community/NetworkManager0.7](https://help.ubuntu.com/community/NetworkManager0.7) 
After doing this restart your machine and post the output of
```
ping -c5 192.168.1.1
```

I applied your methods..
Once type  "ping -c5 192.168.1." the result is "Network is unreachable" :confused:

---

### Post by dineshs on 2010-05-16
please ensure that 
```
gksudo gedit /etc/network/interfaces
``` 
contain only this 
```
auto lo 
iface lo inet loopback
```   
(ref  [http://wiki.debian.org/NetworkManager](http://wiki.debian.org/NetworkManager))

---

### Post by Fibero on 2010-05-26
> **dineshs said:**
> please ensure that 
```
gksudo gedit /etc/network/interfaces
``` 
contain only this 
```
auto lo 
iface lo inet loopback
```   
(ref  [http://wiki.debian.org/NetworkManager](http://wiki.debian.org/NetworkManager))

Sorry for late replay dineshs..I have a problem with my connection.And I forgot my password also.
I did all above. Now it's a little bit improve..Once I opened a browser and type some address, the connection is showing "like" it's gonna be connected. But after view second, it's drop again..
Any chance to solve this issue?

---

