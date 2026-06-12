---
title: "cant connect to broadband!! on 9.10 ..."
date: 2010-03-19
forum: Networking &amp; Wireless
---

### Post by BiiG on 2010-03-19
heyy guyys ...
i cant connect to the broadband .. this wasn't a problem cuz i was on wireless and it connected automatically .. but now am sleeping at a friends house and he doesn't have wireless he only has a broadband Connection ... i plug the Ethernet cable in and it doesn't work .. and when i add a " WIRED " connection it asks for a MAC address ? what do i do ? how do i do it ? plss guyys .. and am kind of a nooByy I've had ubuntu for almost a week . still dont know mucH Yet.. so bare with me please .. :)  

PS: am on a COMPAQ PRESARIO CQ60 -AMD ATHLON X2 64- 4GB RAM - 250HDD .. I've installed ubuntu 9.10 32BIT - through Wubi -

---

### Post by Iowan on 2010-03-19
The MAC address should be available via **ifconfig -a** or **ip link show**. 

> ... so bare with me please ..   I'll pass on getting naked together... ;)

---

### Post by BiiG on 2010-03-19
hahahahahahahahahahah wat the hell man !

so what do i do with MAC address ? should i just copy-paste-apply and thats it ? is there anyway that i cant setup a connection like windows ? on windows i used to connecting through PPoE .. does linux support it ? oh man .. srry for all the questions lolz :P

---

### Post by BiiG on 2010-03-19
................................. no one knows whats going on ?? 
srry i asked... -_-"

---

### Post by wojox on 2010-03-19
You can copy and paste or just type it in and hit Apply.

---

### Post by BiiG on 2010-03-19
hey guys.. this is what showed up .. which one is the mac address ? 

tufa7a@ubuntu:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:1f:16:76:62:db  
          inet6 addr: fe80::21f:16ff:fe76:62db/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:426 (426.0 B)  TX bytes:812 (812.0 B)
          Interrupt:26 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

pan0      Link encap:Ethernet  HWaddr ba:a5:40:a2:34:ad  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:24:2b:cb:6b:3c  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:26 errors:0 dropped:0 overruns:0 frame:0
          TX packets:58 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:16285 (16.2 KB)  TX bytes:7599 (7.5 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-24-2B-CB-6B-3C-00-00-00-00-00-00-00-00-00-00  
          [NO FLAGS]  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

what should i do now ?

---

### Post by BiiG on 2010-03-19
this is with the " ip link show " command :

tufa7a@ubuntu:~$ ip link show
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 16436 qdisc noqueue state UNKNOWN 
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UNKNOWN qlen 1000
    link/ether 00:1f:16:76:62:db brd ff:ff:ff:ff:ff:ff
3: wmaster0: <UP,LOWER_UP> mtu 0 qdisc pfifo_fast state UNKNOWN qlen 1000
    link/ieee802.11 00:24:2b:cb:6b:3c brd 00:00:00:00:00:00
4: wlan0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP qlen 1000
    link/ether 00:24:2b:cb:6b:3c brd ff:ff:ff:ff:ff:ff
6: pan0: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN 
    link/ether ba:a5:40:a2:34:ad brd ff:ff:ff:ff:ff:ff

---

### Post by Iowan on 2010-03-19
> **BiiG said:**
> hey guys.. this is what showed up .. which one is the mac address ? 

tufa7a@ubuntu:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr [COLOR="Red"]00:1f:16:76:62:db[/COLOR]  
          inet6 addr: fe80::21f:16ff:fe76:62db/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:426 (426.0 B)  TX bytes:812 (812.0 B)
          Interrupt:26 Base address:0xc000 

> **BiiG said:**
> this is with the " ip link show " command :

tufa7a@ubuntu:~$ ip link show
...
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UNKNOWN qlen 1000
    link/ether [COLOR="Red"]00:1f:16:76:62:db[/COLOR] brd ff:ff:ff:ff:ff:ff
...MAC address is highlighted in red.

---

### Post by BiiG on 2010-03-19
it wont connect bro.
is there a way to setup a connection ? i mean like a username and a password and stuff like that ?

---

### Post by wojox on 2010-03-19
Did you reboot?

---

### Post by BiiG on 2010-03-19
no id didn't , do i have to ?

---

### Post by BiiG on 2010-03-19
it says connection established .. but nothing opens 

settings are :

IPv4 : link-local only 
IPv6 : link-local only 

what do i do pls ? i cant use my laptop :S

---

### Post by Iowan on 2010-03-19
Link local... Doesn't that get a 169.254.X.X address? You may want to use Automatic (DHCP) or Manual depending on whether your friend's network has DHCP server or not. (It *probably* does).

---

