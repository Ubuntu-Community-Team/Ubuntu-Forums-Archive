---
title: "No connection with router"
date: 2010-04-07
forum: Networking &amp; Wireless
---

### Post by matzuu on 2010-04-07
Hello guys!

I just bought a new router (T[P-Link tl-wr941nd]("http://www.tp-link.com/products/productDetails.asp?class=router&pmodel=TL-WR941ND")) and after trying to configure it I can no longer connect to the internet.

My connections are as follows:

1. Cable Modem's LAN port connected to the router's WAN port;

2. Router's LAN port connected to my desktop PC running karmic.

All of the LEDs on the router are lighting up as specified in the manual.

I tried running the configuration cd that came with the router but i get an error saying the network adapter check failed. Is this setup method supposed to work with windows only?

I also tried the other configuration method that involves opening my browser and connecting to 192.168.1.1, which opens a web based config utility for my router. From here i run a quick setup wizard which I complete successfully, but i still can't get access to the internet.

Any help would be greatly appreciated

---

### Post by chili555 on 2010-04-07
> I also tried the other configuration method that involves opening my browser and connecting to 192.168.1.1, which opens a web based config utility for my router. From here i run a quick setup wizard which I complete successfully, but i still can't get access to the internet.
I think your ethernet interface is still stuck on the IP address you used to connect to the router, perhaps 192.168.1.2. Please try:```
sudo ifconfig eth0 down && sudo ifconfig eth0 up
```Now does the Network Manager applet see your router and allow you to connect? Can you ping the router?```
ping -c3 192.168.1.1
```

---

### Post by matzuu on 2010-04-07
> I think your ethernet interface is still stuck on the IP address you  used to connect to the router, perhaps 192.168.1.2. Please try: 	Code:
 	sudo ifconfig eth0 down && sudo ifconfig eth0 up


I tried this command and i get asked for my password, but somehow I can't input it lol. I type the characters but the cursor doesn't even move.

---

### Post by chili555 on 2010-04-07
For security reasons, your password will not show and it will not even show the number of characters, like ****. Just type it in and hit Enter. If you typed the correct thing, it will take it.

---

### Post by matzuu on 2010-04-07
Lol, sorry about my noobieness.

I entered the command and I got this:

SIOCSIFFLAGS: Permission denied

Two seconds after that a pop-up appeared on the right side of the desktop saying I got disconnected.

---

### Post by chili555 on 2010-04-07
> **matzuu said:**
> Lol, sorry about my noobieness.

I entered the command and I got this:

SIOCSIFFLAGS: Permission denied

Two seconds after that a pop-up appeared on the right side of the desktop saying I got disconnected.Now can you go back to the Network Manager icon and connect properly?

---

### Post by matzuu on 2010-04-07
> **chili555 said:**
> Can you ping the router?```
ping -c3 192.168.1.1
```

If I ping the router after inputting the 1st command I get a message saying the network is unreachable.

Pinging the router before the 1st command gets me this:

```
tiago@Black:~$ ping -c3 192.168.1.1

PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.

64 bytes from 192.168.1.1: icmp_seq=1 ttl=64 time=0.301 ms

64 bytes from 192.168.1.1: icmp_seq=2 ttl=64 time=0.251 ms

64 bytes from 192.168.1.1: icmp_seq=3 ttl=64 time=0.254 ms



--- 192.168.1.1 ping statistics ---

3 packets transmitted, 3 received, 0% packet loss, time 2000ms

rtt min/avg/max/mdev = 0.251/0.268/0.301/0.029 ms
```

> Now can you go back to the Network Manager icon and connect properly? 	

Clicking the Network Manager icon after inputting the 1st command shows me the two 
ethernet controlers that came with my motherboard, but both of them are set as disconnected and unavailable, so I cannot connect.

 Also, my router doesn't show up on the network manager.

BTW, thanks for all the effort :P

---

### Post by Gunman1982 on 2010-04-07
Since you can ping the router and just not get through to the internet it is probably more related to some misconfiguration in the router. So check if the router status page ( [http://192.168.1.1/](http://192.168.1.1/) ) tells you if it is connected to the internet.

---

### Post by Iowan on 2010-04-07
You might ping Internet by IP address (74.125.95.147). If that works, you may have DNS (or routing) issues somewhere between client, router, and modem...

---

### Post by matzuu on 2010-04-08
Hello again everyone.

I just inadvertently solved this one. All it took was a firmware upgrade of my router and cloning the MAC address of my gigabit LAN card to my WAN MAC address, which I had tried before, but I guess it only worked after the firmware upgrade.

A big thank you goes out to all you guys for trying to help me.

---

