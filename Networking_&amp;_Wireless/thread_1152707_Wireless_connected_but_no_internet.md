---
title: "Wireless connected but no internet"
date: 2009-05-08
forum: Networking &amp; Wireless
---

### Post by elpichi on 2009-05-08
Hello, I'm having very frustrating time with my wireless connection in xubuntu 64bit. The network manager seems to be managing the device just fine. It is able to get an IP from the router and it has the correct dns and gateway addresses. I have tried disabling all interfaces, editing the routing tables and the iptables firewall is accepting all requests. If anyone has any idea why am i not able to get any response from launchmodem.com please help me. thanks in advance.

---

### Post by chili555 on 2009-05-08
> i not able to get any response from launchmodem.comI'll bet your internet service provider is AT&T. When you are initially set up with AT&T, the modem/router/wireless appliance hands out a DNS address that is supposed to redirect any request into the setup pages of the modem. You are then able to enter your username and password, set up wireless encryption, etc.

I've never had any luck getting launchmodem.com to redirect. I suspect it's Internet Explorer-centric. Instead, open up Firefox and put in [http://192.168.1.254](http://192.168.1.254). You should then get to the modem's setup pages and make the necessary entries. You will also find a button to order the modem to connect to the AT&T network, which it should do easily if you have the correct username and password entered. After you have all this set up, Please:```
sudo gedit /etc/resolv.conf
```Change the nameserver from launchmodem.com to:```
nameserver 192.168.1.254
```Now, if you are not using AT&T as I guessed, the procedure should be very similar.

---

### Post by elpichi on 2009-05-14
You are right it is At&t but the modem is working fine under windows. Here is the situation, i'm receiving wireless from a router connected to the modem, I changed the router's IP so it would not conflict with the modem's.
the dhcp server IP supplied by the router is: 90.20.150.2
and the dns IP from the modem is: 192.168.2.254

maybe i have to supply some extra info within the system to get it working?

---

### Post by superprash2003 on 2009-05-15
are you able to ping 209.85.171.100

---

### Post by elpichi on 2009-05-15
not at all 
says: from 90.20.150.100 icmp_seq=x Destination Host Unreachable

---

### Post by chili555 on 2009-05-15
> the dhcp server IP supplied by the router is: 90.20.150.[COLOR="Red"]2[/COLOR]> from 90.20.150.[COLOR="Red"]100[/COLOR] icmp_seq=x Destination Host UnreachableI don't quite undestand this. The router asks the modem for an IP address and gets 192.168.2....what? Then your computer asks the router for an IP address and gets...what? x.2 or x.100?

---

### Post by elpichi on 2009-05-20
Oh cheese, i can see your confusion, and i seriously don't know what's going on with that. the gateway for the router is x.2 and is looking for x.100.
The router's IP pool starts at: 90.20.150.100 up to x.x.x.150.

---

### Post by superprash2003 on 2009-05-20
post an output of** ifconfig** and **sudo iptables -L** from the terminal

---

### Post by elpichi on 2009-05-25
Sorry for my late reply, here is the ouput:

[http://img41.imageshack.us/img41/3039/ifconfig.jpg](http://img41.imageshack.us/img41/3039/ifconfig.jpg)

---

### Post by superprash2003 on 2009-05-26
in your terminal type **sudo ifdown eth0** and **sudo ifdown wmaster0** . now try** ping 209.85.171.100**

---

### Post by elpichi on 2009-05-26
for each of them says:
ifdown: interface wmaster0 not configured 
ifdown: interface eth0 not configured :(

and still complains about destination host unreachable when pinging that ip.

---

### Post by superprash2003 on 2009-05-26
post contents of your /etc/network/interfaces file.

---

