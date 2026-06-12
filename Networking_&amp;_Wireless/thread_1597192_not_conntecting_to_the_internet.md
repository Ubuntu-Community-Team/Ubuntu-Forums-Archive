---
title: "not conntecting to the internet"
date: 2010-10-15
forum: Networking &amp; Wireless
---

### Post by baburi on 2010-10-15
hey guys im very new to ubuntu just kicked windows for ubuntu and everything installed fine. But firefox will not open anything other then my gateway page 10.0.0.38
and that is after i manually put my addresse in. and nslook up isnt doing anything for me.
someone help:( 


btw im using eth0

---

### Post by baburi on 2010-10-15
also im using ubuntu 10.4
should i just install 10.10? or the problem will still be there?

---

### Post by lovinglinux on 2010-10-15
Have you tried to disable ipv6? See the fifth item on [this list]("http://firefox-tutorials.blogspot.com/2010/05/common-issues-solutions.html").

---

### Post by baburi on 2010-10-16
yep all ready done that and still nothing. :S

---

### Post by lovinglinux on 2010-10-16
Can you reach any site via IP?

---

### Post by baburi on 2010-10-17
no i can only get to my gateways page  from my provider bigpond page  IP 10.0.0.138

---

### Post by krishnandu.sarkar on 2010-10-17
Well...I'd say configure your router to PPPoE. This saves lots of hassles.

---

### Post by baburi on 2010-10-17
The router is not the problem, all other machines on the network can browse the internet fine. I think the problem lies in Ubuntu because when I had windows on this machine before my internet connection was flawless

---

### Post by krishnandu.sarkar on 2010-10-17
I didn't said there is a problem with your router. I just said configure your router to PPPoE. That would save lots of hassels, because any OS you install, you'll be connected to internet by just switching on the router, even just connecting a laptop or PC with the router gets you internet. Means you don't have to configure your settings anywhere else.

---

### Post by baburi on 2010-10-17
hey guys im very new to ubuntu just kicked windows for ubuntu and everything installed fine. But firefox will not open anything other then my gateway page 10.0.0.38
and that is after i manually put my addresse in. and nslook up isnt doing anything for me.
someone help:sad: 


btw im using eth0



The router is not the problem, all other machines on the network can browse the internet fine. I think the problem lies in Ubuntu because when I had windows on this machine before my internet connection was flawless.

---

### Post by krishnandu.sarkar on 2010-10-17
Why did you created two thread for same reason..??

[http://ubuntuforums.org/showthread.php?t=1597192](http://ubuntuforums.org/showthread.php?t=1597192)

---

### Post by baburi on 2010-10-17
my router is a modem router in one, and it's from Bigpond as well so It's pretty locked up and not much looks changable

---

### Post by krishnandu.sarkar on 2010-10-17
Go to your router's IP, it would ask for username and password(if you didn't selected for remember), now on wan page see it's configured in bridge mode, just change it to PPPoE, and provide your login username and password there. And finally restart the router.

---

### Post by baburi on 2010-10-17
no go :( would not allow me to change any of it.

---

### Post by luctor on 2010-10-17
what's the output of ifconfig

---

### Post by krishnandu.sarkar on 2010-10-17
Ohh....sorry then leave it.

Is internet working from Live CD..??

---

### Post by baburi on 2010-10-17
ifconfig looks fine 
gets its self an ip address:10.0.0.38 and  255.255.255.0 bcast 10.0.0.255
no loop-back or anything like that

and i have not  tryed live cd yet.

---

### Post by krishnandu.sarkar on 2010-10-17
Didn't you said 10.0.0.38 is your Router's IP(Gateway)..??

Well, first do what [luctor]("http://ubuntuforums.org/member.php?u=283356") said.

Go to terminal > ifconfig
Copy the output and paste it here(Within CODE tags please) or use pastebin to paste the output and share the link.

---

### Post by baburi on 2010-10-17
eth0 Link encap:Ethernet HWaddr 00:13:d4:16:57:c2
inet addr:10.0.0.38 Bcast:10.0.0.255 Mask:255.255.255.0
inet6 addr: fe80::213:d4ff:fe16:57c2/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:2002 errors:0 dropped:0 overruns:0 frame:0
TX packets:1695 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:166528 (166.5 KB) TX bytes:160071 (160.0 KB)
Interrupt:19 Base address:0xd400
lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:8 errors:0 dropped:0 overruns:0 frame:0
TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:480 (480.0 B) TX bytes:480 (480.0 B)



and sorry typoo 10.0.0.138 is my routers ippage

---

### Post by krishnandu.sarkar on 2010-10-17
Can you ping google or other site..??

---

### Post by baburi on 2010-10-17
nope :(

---

### Post by krishnandu.sarkar on 2010-10-17
Well...check with the Live CD if you can access internet..??

---

### Post by baburi on 2010-10-17
nope......

---

### Post by dineshs on 2010-10-17
What do you get for
```
ping 4.2.2.1 -c4
```?
How did you configure manual IP?via network manager?

---

