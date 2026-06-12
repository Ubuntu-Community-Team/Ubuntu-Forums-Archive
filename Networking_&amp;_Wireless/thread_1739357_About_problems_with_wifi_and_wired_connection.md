---
title: "About problems with wifi and wired connection"
date: 2011-04-25
forum: Networking &amp; Wireless
---

### Post by vladence on 2011-04-25
Hi. I am using ADSL internet trough a standard modem using the pppoe protocol with username and password.

How ever I managed to install wireless router and everything was ok until i put a cable from the router to the laptop i.e i replaced the main Internet cable with another from the router to the laptop.

Now to problem is that when I want to put the main Internet cable directrly to my lapto and connect mannualy with username and pass it is giving me that it is connected but the eth0 interface has address 0.0.0.0. weird stuff.

Also I think that the router is acting as a pppoe router because wher this command is entered in terminal sudo ip addr,  I get this output

```

1: lo: <LOOPBACK,UP,LOWER_UP> mtu 16436 qdisc noqueue state UNKNOWN     
 link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00     
 inet 127.0.0.1/8 scope host lo  
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP qlen 1000      
link/ether 00:1e:33:0a:11:75 brd ff:ff:ff:ff:ff:ff  
3: wlan0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc pfifo_fast state DOWN qlen 1000     
 link/ether 00:16:44:ec:8c:dc brd ff:ff:ff:ff:ff:ff  
5: ppp0: <POINTOPOINT,MULTICAST,NOARP,UP,LOWER_UP> mtu 1492 qdisc pfifo_fast state UNKNOWN qlen 3     
 link/ppp      
 inet 192.168.16.100 peer 46.217.20.1/32 scope global ppp0
```

192.168.16.100 is like the addresses that the router is giving. I doesnt look like a normal WAN address.

Any help would be apreciated, thanks Vlad

---

### Post by byStanderone on 2011-04-25
How ever I managed to install wireless router and everything was ok until i put a cable from the router to the laptop i.e i replaced the main Internet cable with another from the router to the laptop

*...would it be correct to say that you are using the lan connection, as per your statement above? that is router's lan output to your laptop's lan port...

---

### Post by vladence on 2011-04-26
Yup that is correct. Why my eth0 interface doesn't work. It is giving me address 0.0.0.0 when I put the main WAN cable directly to the laptop?

---

### Post by lz1dsb on 2011-04-26
If you're using ADSL with PPoE, than you'll need additional configuration on your interface in order to work. The reason it works when you're using a router is because the router does that for you. (the PPoE encapsulation and the authentication with username and password)

---

