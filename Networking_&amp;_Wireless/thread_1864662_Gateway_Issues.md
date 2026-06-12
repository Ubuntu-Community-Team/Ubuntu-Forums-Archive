---
title: "Gateway Issues"
date: 2011-10-19
forum: Networking &amp; Wireless
---

### Post by patmaster on 2011-10-19
Hi,   I have 3 ubuntu 10.4 machines here.  One acts as a gateway and the other 2 should use that gateway to connect to the internet. The whole thing is put together over our form-network that i dont administrate and i have no idea about.   Now i have setup the gateway and it is working for one machine but not for the other.  here's what i got:  gateway = 10.122.64.219 machine a = 10.122.65.19 (it uses the gw and connects to the internet) machine b = 10.122.65.220 (seems to use the gw but it cant connect to the internet)  Can somebody plz help me make this work ?!

---

### Post by jemate18 on 2011-10-19
> **patmaster said:**
> Hi,   I have 3 ubuntu 10.4 machines here.  One acts as a gateway and the other 2 should use that gateway to connect to the internet. The whole thing is put together over our form-network that i dont administrate and i have no idea about.   Now i have setup the gateway and it is working for one machine but not for the other.  here's what i got:  gateway = 10.122.64.219 machine a = 10.122.65.19 (it uses the gw and connects to the internet) machine b = 10.122.65.220 (seems to use the gw but it cant connect to the internet)  Can somebody plz help me make this work ?!

Please give more info.

1. Did you set /proc/sys/net/ipv4/ip_forward value to 1?
2. Do you use iptables or UFW for your firewall configurations?
3. Did you setup the private and public interface for the gateway machine correctly?

Best,

---

### Post by patmaster on 2011-10-19
> **jemate18 said:**
> Please give more info.

1. Did you set /proc/sys/net/ipv4/ip_forward value to 1?
2. Do you use iptables or UFW for your firewall configurations?
3. Did you setup the private and public interface for the gateway machine correctly?

Best,

1. Yes i did  (like i said, it works for one machine)
2. What is UFW ?! To be honest i can't really tell because it's been some time and even back then i just googled my way there. Is there anyway i can check this ?!
  3. I only have one Interface on each of the systems. What settings exactly do you want to see ?!  I'm more than willing to give you all the information you nedd but I'm a unix newbie so you'll have to tell me where to find it :(

---

### Post by jonobr on 2011-10-19
Hey there

I would like to see how you have subnetted these interfaces

Can you post the results of /etc/network/interfaces?

also ifconfig would be good

---

### Post by e79 on 2011-10-19
Also do a 

```
cat /etc/resolv.conf
```

on both machines

---

### Post by patmaster on 2011-10-20
Okay here from the machine that **successfully** uses the gateway:

/etc/network/inferaces
```
auto lo
iface lo inet loopback
```ifconfig:

```
eth1      Link encap:Ethernet  Hardware Adresse 00:0c:6e:b8:cd:ec  
          inet Adresse:10.122.65.19  Bcast:10.122.65.255  Maske:255.255.254.0
          inet6-Adresse: fe80::20c:6eff:feb8:cdec/64 Gültigkeitsbereich:Verbindung
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metrik:1
          RX packets:320753 errors:0 dropped:0 overruns:0 frame:0
          TX packets:211257 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000 
          RX bytes:29828047 (29.8 MB)  TX bytes:177512580 (177.5 MB)

lo        Link encap:Lokale Schleife  
          inet Adresse:127.0.0.1  Maske:255.0.0.0
          inet6-Adresse: ::1/128 Gültigkeitsbereich:Maschine
          UP LOOPBACK RUNNING  MTU:16436  Metrik:1
          RX packets:4369 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4369 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:0 
          RX bytes:1367669 (1.3 MB)  TX bytes:1367669 (1.3 MB)

```cat /etc/resolve.conf:

```
search orac.local
nameserver 10.122.64.201
```Here from the machine where i can not get a connection to the internet:

/etc/network/inferaces
```
auto lo
iface lo inet loopback
```ifconfig:

```
eth0      Link encap:Ethernet  Hardware Adresse 00:1b:21:bd:72:a9  
          inet Adresse:10.122.64.220  Bcast:10.122.65.255  Maske:255.255.254.0
          inet6-Adresse: fe80::21b:21ff:febd:72a9/64 Gültigkeitsbereich:Verbindung
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metrik:1
          RX packets:177388 errors:0 dropped:0 overruns:0 frame:0
          TX packets:50373 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:14905 Sendewarteschlangenlänge:100 
          RX bytes:14218208 (14.2 MB)  TX bytes:55421505 (55.4 MB)
          Speicher:df3c0000-df3e0000 

eth1      Link encap:Ethernet  Hardware Adresse 78:2b:cb:4a:cd:d0  
          UP BROADCAST MULTICAST  MTU:1500  Metrik:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 Speicher:da000000-da012800 

eth2      Link encap:Ethernet  Hardware Adresse 78:2b:cb:4a:cd:d1  
          UP BROADCAST MULTICAST  MTU:1500  Metrik:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 Speicher:dc000000-dc012800 

lo        Link encap:Lokale Schleife  
          inet Adresse:127.0.0.1  Maske:255.0.0.0
          inet6-Adresse: ::1/128 Gültigkeitsbereich:Maschine
          UP LOOPBACK RUNNING  MTU:16436  Metrik:1
          RX packets:63 errors:0 dropped:0 overruns:0 frame:0
          TX packets:63 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:0 
          RX bytes:4436 (4.4 KB)  TX bytes:4436 (4.4 KB)


```cat /etc/resolve.conf:

```
search orac.local
nameserver 10.122.64.201
```Thx for your help !

Do you need anything else ?!

I just did a tracepath on both machines and the look exactly the same and both of them seem to be using the gateway. 
Also it seems that only a specific ip is allowed to connect to the internet. The machine that has it is able to connect. 
My guess is that there is a problem with the gw itself. 


Could someone tell me what configs i should check ?!

---

### Post by e79 on 2011-10-20
> Also it seems that only a specific ip is allowed to connect to the internet.Is it possible your gateway only allow specific range of IPs to get on the internet ? On your second machine, was the IP distributed through DHCP or you set it manually ? Is a firewall/router blocking connections would be also plausible ?

As far as I'm concerned, your configs looks OK to me.

---

### Post by patmaster on 2011-10-20
Okay i got it. 
It seems that i used the wrong interface in iptables. 

Thanks for all your answers !

---

### Post by e79 on 2011-10-20
I'm glad you could resolve your issue. Please mark the thread as solved (using the Thread Tools) if you feel it is.

Regards

---

### Post by jonobr on 2011-10-20
Before you shut up shop , I asked for sub netting info as there is a lot of folks on these forums who change around broadcast adddress and subnets and are not really sure of what they are doing, hence me asking.

I just want to let you know that your subnet that you have created and the mask all look ok, but wanted to point out that your valid hosts for  the ETH1 interface would be in the 10.122.64.1 - 10.122.65.254 range.
If your aware of that, then Ill just get my hat and coat and move move on :p

---

