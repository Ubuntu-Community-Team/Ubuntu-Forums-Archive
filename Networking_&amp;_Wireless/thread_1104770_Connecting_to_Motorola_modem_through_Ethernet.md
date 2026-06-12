---
title: "Connecting to Motorola modem through Ethernet"
date: 2009-03-23
forum: Networking &amp; Wireless
---

### Post by shizumasa14 on 2009-03-23
Hello, I have Windows XP on a shared Desktop and Ubuntu on my personal laptop.  We just bought a new modem and moved the Desktop.  I now want to connect my laptop to the motorola modem.  I plug it in and I can't figure out what to do.  Please help?

---

### Post by shizumasa14 on 2009-03-26
Can someone help me please?

---

### Post by superprash2003 on 2009-03-26
in your terminal type **ifconfig** and post output.. in windows did you require to setup any ip information?

---

### Post by shizumasa14 on 2009-03-27
Not in windows, no.  I will try what you said.

---

### Post by shizumasa14 on 2009-03-29
shizumasa14@shizumasa14-laptop:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:1e:ec:d7:2a:d8  
          inet6 addr: fe80::21e:ecff:fed7:2ad8/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:797 errors:0 dropped:700887910 overruns:0 frame:0 
          TX packets:11 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:56694 (56.6 KB)  TX bytes:2178 (2.1 KB) 
          Interrupt:218 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:264 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:264 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:16904 (16.9 KB)  TX bytes:16904 (16.9 KB) 

shizumasa14@shizumasa14-laptop:~$



Also, my mistake.  It is an ARRIS modem.  We used to have a motorola one.

---

### Post by shizumasa14 on 2009-03-30
can someone help me please!!

---

### Post by Hobgoblin on 2009-03-30
If it's an ethernet modem then you shouldn't have to do anything, it's basically a single port router.

What did you when you connected it to the Windows system?

---

### Post by shizumasa14 on 2009-03-30
I never connected it to windows through Ethernet.  I used my dads wireless network (he lives next to me).  But when I switched to ubuntu I never figured out how to do it, so I went out and bought a modem.

---

### Post by superprash2003 on 2009-04-01
do you know your modems ip address?? post output of ipconfig from windows command prompt.

---

