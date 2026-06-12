---
title: "Firefox/Opera problems (Connecting slowly)"
date: 2009-04-19
forum: Networking &amp; Wireless
---

### Post by Motw on 2009-04-19
Hey guys,

Im pretty new to Ubuntu and I must say I love this OS, however theres a few things bothering me. I fixed most of the things that didnt work for me, but I cant seem to find a working solution for this problem.

Whenever I browse the net Im getting annoyed by how slow my browsers connect. It seems to be only the connecting, because whenever Im connected to a server the pages from the same server go faster than the first page.

It isnt a system failure as Firefox was fast when I used XP, it isnt my connection as I didnt switch ISP. So I guess its something in Ubuntu.

Im puzzled. Would anyone know how I could fix this problem?

Thanks in advance,

Robin.

---

### Post by superprash2003 on 2009-04-19
post output of **ifconfig** from the terminal . also try disabling ipv6 [http://www.prash-babu.com/2009/01/how-to-disable-ipv6-in-linux-ubuntu-to.html](http://www.prash-babu.com/2009/01/how-to-disable-ipv6-in-linux-ubuntu-to.html)

---

### Post by prshah on 2009-04-19
> **Motw said:**
> 
Whenever I browse the net Im getting annoyed by how slow my browsers connect. It seems to be only the connecting, because whenever Im connected to a server the pages from the same server go faster than the first page.

See [[SOLVED] Firefox/Epiphany/Lynx not loading certain websites]("http://ubuntuforums.org/showthread.php?t=718709") for a possible solution. (You'll have to read thru to the very end; or you can just jump to the end if you're impatient).

---

### Post by Motw on 2009-04-19
> **superprash2003 said:**
> post output of **ifconfig** from the terminal . also try disabling ipv6 [http://www.prash-babu.com/2009/01/how-to-disable-ipv6-in-linux-ubuntu-to.html](http://www.prash-babu.com/2009/01/how-to-disable-ipv6-in-linux-ubuntu-to.html)

if I run ifconfig, then the terminal closes right away.

I already disabled ipv6 in Firefox and it makes no difference, so that shouldnt be it. Anyway I followed the steps done there. Ill see if it helped tomorrow (Gotta get to bed now).

Anyway, thanks for the ideas. :)

---

### Post by Motw on 2009-04-19
> **prshah said:**
> See [[SOLVED] Firefox/Epiphany/Lynx not loading certain websites]("http://ubuntuforums.org/showthread.php?t=718709") for a possible solution. (You'll have to read thru to the very end; or you can just jump to the end if you're impatient).

Read it, the solution was changing MTU from 1500 to 1492, but thats a router problem.. I didnt have that problem with XP and downstairs my dad browses fast with vista (He hasnt seen the light yet).

I believe this wont help, but Ill try it tomorrow anyway.

Thanks for the ideas :)

---

### Post by Motw on 2009-04-20
> **superprash2003 said:**
> post output of **ifconfig** from the terminal . also try disabling ipv6 [http://www.prash-babu.com/2009/01/how-to-disable-ipv6-in-linux-ubuntu-to.html](http://www.prash-babu.com/2009/01/how-to-disable-ipv6-in-linux-ubuntu-to.html)

k now I did it using the menu instead of alt-f2 and this is the output;

> robin@Robin:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:11:09:da:0f:92  
          inet addr:192.168.10.101  Bcast:192.168.10.255  Mask:255.255.255.0
          inet6 addr: fe80::211:9ff:feda:f92/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:17830 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14725 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:17044714 (17.0 MB)  TX bytes:2675586 (2.6 MB)
          Interrupt:23 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

Edit: Yea, the MTU is 1500 I really should see if changing that makes any difference. Big thanks guys, this is probably what ****s it all up.

Edit2: Alright I changed it to 1492 and I dont notice any changes yet, but Ill see what happens when I reset my router.

---

### Post by prshah on 2009-04-21
> **Motw said:**
> I didnt have that problem with XP and downstairs my dad browses fast with vista (He hasnt seen the light yet).

I didn't have any problem with XP either, as mentioned in the linked thread. XP worked just as well with 1500 MTU as with 1492 MTU; but in Ubuntu browsing was terrible with router set to MTU 1500.

---

### Post by Motw on 2009-04-21
Mmm I didnt manage to change it to 1492 yet. I used a ifconfig to temporarily change it, but I have no clue how to do this permanently.

I guess the problems solved, but I hope you could explain me how to change the MTU :)

Cheers, Robin.

---

### Post by prshah on 2009-04-21
> **Motw said:**
> I used a ifconfig to temporarily change it, but I have no clue how to do this permanently.

My "fix" recommends changing the ROUTER's WAN interface MTU to 1492; I've never checked if changing the Ubuntu system's MTU works or not. I do know that if I _match_ MTUs on the system and the router, the browsing troubles start again. Eg, Though my router's WAN interface MTU is 1492, my ubuntu box MTU is 1500.

To change the router's MTU you need to access the routers configuration page, which varies from model to model, but usually: Just open a browser, and in the address bar, type [http://192.168.1.1](http://192.168.1.1)

However, if you are not too techy, I don't advise doing this yourself, as you may lose out on Internet connectivity if you end up changing any other settings.

If you find that just changing the MTU on your system works fine, then you can make it permanent; post back with your ubuntu version for exact details: To find out what version you are using, open a terminal (Applications-Accessories-Terminal) and give the command ```
lsb_release -a
```

---

### Post by Motw on 2009-04-21
Alright Ive been looking for ways to change it..

-Terminal refuses to change the MTU to 1492 again, for some reason
-Even if I could I wouldnt change it permanently and Id have to edit ect/network/interface, but its read-only and I dont have permission to edit it.
-Whenever Im trying to connect to 192.168.1.1 Ive got a network timeout. 192.168.1.1 takes too long to respond..

Anyway heres the output;
> robin@Robin:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 9.04
Release:	9.04
Codename:	jaunty

---

### Post by Motw on 2009-04-21
I managed to set the MTU to 1492 by setting it in the settings of eth0. (Wow never thought itd be that simple) However theres no changes yet..

Reboot time, second. =)

Edit; Mmmhm nothing. Still the same lame internet after changing the MTU in Ubuntu.

---

### Post by Motw on 2009-04-27
Nothing yet =/ Anyone else having an idea?

---

