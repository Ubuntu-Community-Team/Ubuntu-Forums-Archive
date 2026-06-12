---
title: "Can't connect to internet"
date: 2011-02-10
forum: Networking &amp; Wireless
---

### Post by Mainewha on 2011-02-10
I don't know about everyone else but I have a weird thing going. I managed to install Ubuntu last night, even got the updates downloaded. but for some reason I am unable to connect to the internet otherwise. I would appreciate any and all help on this matter.

TL/DR: HELP!

---

### Post by TBABill on 2011-02-10
Can you provide some more information? Are you trying by wired ethernet or wireless? Does one way work and not the other? Can you install updates but just not browse in Firefox? Are other browsers installed and/or working?
 
Any extra you can provide will help greatly in narrowing down the possibilities.

---

### Post by grahammechanical on 2011-02-10
How do you know that you cannot connect to the Internet? Tell us what messages you get. Tell us what you have tried to do. It will give us a clue as to what is not working.

Regards.

---

### Post by Mainewha on 2011-02-10
> **TBABill said:**
> Can you provide some more information? Are you trying by wired ethernet or wireless? Does one way work and not the other? Can you install updates but just not browse in Firefox? Are other browsers installed and/or working?
 
Any extra you can provide will help greatly in narrowing down the possibilities.


For now wired ethernet. And I have no success either way (wired or wireless). Yes I can install updates but not browse in firefox. No other browsers are installed. The link on your sig notes that my model laptop is supported.

---

### Post by Mainewha on 2011-02-10
> **grahammechanical said:**
> How do you know that you cannot connect to the Internet? Tell us what messages you get. Tell us what you have tried to do. It will give us a clue as to what is not working.

Regards.


The browser fails to connect. Now I know all of my equipment is in working order, otherwise I wouldnt be able to post this reply. (the laptop in question is roughly 3 feet behind me)

---

### Post by Mainewha on 2011-02-10
lebump

---

### Post by Mainewha on 2011-02-11
bump again

---

### Post by weblizist on 2011-02-11
You need to follow kind of standard troubleshouting

is your interface up? Is routing in place? Are you able to ping your default gateway? Does DNS resolution work? Are you using iptables or any other local firewall? Does another computer reach the Internet using the same network cable? ...

ever run "ipconfig, netstat -rn, tcpdump" or alike?

---

### Post by kimberlite on 2011-02-11
Hi, post the output of "ifconfig" command.

---

### Post by Mainewha on 2011-02-11
> **weblizist said:**
> You need to follow kind of standard troubleshouting

is your interface up? Is routing in place? Are you able to ping your default gateway? Does DNS resolution work? Are you using iptables or any other local firewall? Does another computer reach the Internet using the same network cable? ...

ever run "ipconfig, netstat -rn, tcpdump" or alike?

> **kimberlite said:**
> Hi, post the output of "ifconfig" command.




Part 1: Going to need a little guidance before I can go that far (as in where to put that in) but the cable is fine and works as it should.


Part 2: ok here's the results as I know them:

mainewha@mainewha-Inspiron-1525:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1d:09:54:a2:e6  
          inet addr:192.168.0.108  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:9ff:fe54:a2e6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2003 errors:0 dropped:0 overruns:0 frame:0
          TX packets:720 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:959060 (959.0 KB)  TX bytes:67206 (67.2 KB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:32 errors:0 dropped:0 overruns:0 frame:0
          TX packets:32 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2256 (2.2 KB)  TX bytes:2256 (2.2 KB)

---

### Post by kimberlite on 2011-02-12
First, try to follow instructions from here:
[https://help.ubuntu.com/8.04/internet/C/network-troubleshooting.html]("https://help.ubuntu.com/8.04/internet/C/network-troubleshooting.html")

---

### Post by AlexDudko on 2011-02-12
Maybe **File -> Work Offline** in Firefox is selected?

---

### Post by yashar on 2011-02-12
go to EDIT>dereference>Connection

and check for connection type, it should be auto, or use system proxy.

---

### Post by Mainewha on 2011-02-13
Ok. it appears that for some reason the blame can all be laid at the feet of Firefox.....I don't know why it would fail so spectacularly on a system it seems perfect for but it did. so I nixed that and put in Chromium. Now I just need to get flash working and I am set (but thats a different forum)

---

