---
title: "hughes satellite internet"
date: 2009-06-29
forum: Networking &amp; Wireless
---

### Post by joel383 on 2009-06-29
I'm a noob to ubuntu, but i'm trying to learn. 

i install satellite Internet (hughes-net) and one of the requirements during set up is to access the modems built in interface to point the dish. to get to it you have to load 169.254.0.1. only problem is firefox won't load the page. once the modem is set up through another computer, i can connect to the 192.168.0.1 modem status page just fine, and cruise the interwebs just fine.

i'm thinking that it cant establish a connection with the modem when the modem is not connected with the NOC ([FONT=Times][SIZE=3][COLOR=#231f20][COLOR=#231f20][FONT=Times]Network Operations Center[/FONT][/COLOR][/COLOR][/SIZE][/FONT])
using:
firefox
gnome 2.24.1
ubuntu 9.04

---

### Post by jonobr on 2009-06-29
Hello

Welcome to the forums,
I think your a bit all over the road here.

It sounds as if your windows (or other box) is connecting using 192.168 address.

Could you tell us your set up now?

What the IP address of the router your connecting to?
Is is 192.168.0.1?

Whats the ip address of the other computer,
whats the ip address of your ubuntu box?

you can find this out by 
going to applications->accessories-> terminal

type ifconfig and post the results.

---

### Post by computer13137 on 2009-06-29
I have never found a solution to this problem... 

I don't have HughesNet, I have Motorola Canopy, but my antenna status page is on 169.254.1.1.  For some reason, Ubuntu will not properly route 169 addresses it seems to me.

Try accessing the page on a Windows XP system.  Windows Vista and Ubuntu have never been able to see my antenna's status page on 169.254.1.1, but XP can see them just fine (even routed through my Ubuntu router).

If this is not a possibility, plug the Ubuntu box in as directly as you can.  My Ubuntu router upstairs can access and ping 169.254.1.1, but my Ubuntu system downstairs can not because it's not directly plugged in.  I'm not sure what the complexities of this are, but if you plug in really directly, or use an XP computer, it should work.

You might also try assigning a static IP address to your Ubuntu system like 169.254.0.5 and then trying to access the page.

I'm subscribing to this thread since I think I can help you resolve this problem.

-Kirk

---

### Post by joel383 on 2009-06-29
> **jonobr said:**
> Hello

Welcome to the forums,
I think your a bit all over the road here.

It sounds as if your windows (or other box) is connecting using 192.168 address.

Could you tell us your set up now?

What the IP address of the router your connecting to?
Is is 192.168.0.1?

Whats the ip address of the other computer,
whats the ip address of your ubuntu box?

you can find this out by 
going to applications->accessories-> terminal

type ifconfig and post the results.

no router

by default the modems come out of the box with a set up wizard at the 169.254.0.1 address accessed from firefox or other browser.

then after it is "commissioned" it defaults to the 192.168.0.1 address.

currently i'm on the office wifi... here are the results:
```
joel@joel-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:12:f0:83:43:8e  
          inet addr:192.168.10.106  Bcast:192.168.10.255  Mask:255.255.255.0
          inet6 addr: fe80::212:f0ff:fe83:438e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:376149 errors:3 dropped:3 overruns:0 frame:0
          TX packets:238284 errors:0 dropped:6 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:560486198 (560.4 MB)  TX bytes:33974390 (33.9 MB)
          Interrupt:5 Base address:0xa000 Memory:fafff000-faffffff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:27 errors:0 dropped:0 overruns:0 frame:0
          TX packets:27 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2095 (2.0 KB)  TX bytes:2095 (2.0 KB)
 
```

i have to go do some service calls so i will try the ifconfig command and try and post the results

---

### Post by computer13137 on 2009-06-29
Maybe you were writing your reply for 8 minutes and didn't see mine.  I'm telling you... Ubuntu will not route 169 addresses properly. lol. :P

-Kirk

---

### Post by joel383 on 2009-06-29
> **computer13137 said:**
> I have never found a solution to this problem... 

I don't have HughesNet, I have Motorola Canopy, but my antenna status page is on 169.254.1.1.  For some reason, Ubuntu will not properly route 169 addresses it seems to me.

Try accessing the page on a Windows XP system.  Windows Vista and Ubuntu have never been able to see my antenna's status page on 169.254.1.1, but XP can see them just fine (even routed through my Ubuntu router).

If this is not a possibility, plug the Ubuntu box in as directly as you can.  My Ubuntu router upstairs can access and ping 169.254.1.1, but my Ubuntu system downstairs can not because it's not directly plugged in.  I'm not sure what the complexities of this are, but if you plug in really directly, or use an XP computer, it should work.

You might also try assigning a static IP address to your Ubuntu system like 169.254.0.5 and then trying to access the page.

I'm subscribing to this thread since I think I can help you resolve this problem.

-Kirk


yeah vista has problems with the modem set up too, thats why i have to have a working laptop.

xp works fine though same as your situation

---

### Post by joel383 on 2009-06-29
> **computer13137 said:**
> Maybe you were writing your reply for 8 minutes and didn't see mine.  I'm telling you... Ubuntu will not route 169 addresses properly. lol. :P

-Kirk


yeah i'm loading the van up to do some service calls i'll try to check in later if you find a work around for the 169 routing     ):P

---

### Post by computer13137 on 2009-06-29
Ah, I misunderstood your initial question.  I thought you were desperately trying to configure your Internet and didn't know what to do... I didn't realize that you were aware of Ubuntu's problems with routing 169 addresses.  My bad. :P

I'll look into it, but I'm not sure I'll find anything.  I'm having a lot of fun answering other questions right now, so I'm just going to keep doing that for the time being. :P  I'm still subscribed to this thread though.

-Kirk

---

### Post by jonobr on 2009-06-29
HI Guys

SOunds as if you guys have more hands on experience, however, one thing I notice,

you mention your pc has a 192.168.1.x address and the router is 192.168.0.x address.

The subnet mask is 255.255.255.0,
that means that you have two devices configured as if they were on two seperate routers.

the first network is the 192.168.1.x network, and then 192.168.0.x network.

I think you should have your pcs etc set to 192.168.0 address and not .1

Cheers

---

### Post by Polaris96 on 2009-06-29
problems routing to 169 addresses?  I'm slightly skeptical that one particular number of 2^8 possibilties is cursed ONLY in the one of four possible "dotted decimal" positions.

I'm not saying your problems aren't real, but "Ubuntu CAN'T route 169 addresses" doesn't make any sense from a networking viewpoint.  I'm going to grab some 169 addresses just to make sure, but I doubt the number 169 is the problem.

---

### Post by puppywhacker on 2009-06-29
the number 169.254 is used for avahi auto discovering services, windows uses them as auto assign an interface. So if you have problems, check mdns / avahi services, if you don't use them, kill the processes.

---

### Post by joel383 on 2009-06-29
> **jonobr said:**
> HI Guys

SOunds as if you guys have more hands on experience, however, one thing I notice,

you mention your pc has a 192.168.1.x address and the router is 192.168.0.x address.

The subnet mask is 255.255.255.0,
that means that you have two devices configured as if they were on two seperate routers.

the first network is the 192.168.1.x network, and then 192.168.0.x network.

I think you should have your pcs etc set to 192.168.0 address and not .1

Cheers

[jonobr]("http://ubuntuforums.org/member.php?u=197514") no router, just a modem...

[computer13137]("http://ubuntuforums.org/member.php?u=863782")  unforturnately you were correct in your initial assumption

---

### Post by jonobr on 2009-06-29
joel383 I think you might have misunderstood my post,

having two separate subnets 
(192.168.0.x and 192.168.1.x) requires a router for the two devices to talk to each other.

if they are all on the same segment then =your devices should either be 192.168.1.x or 192.168.0.x not a mix.

if the subnet mask was a class b , 255.255.0.0 then that would work, but at the moment, the two are not logically on the same network.

However, as said, I have not used this device before so I will get back in my box.

Sorry if my original post confused

CHeers and good luck

---

