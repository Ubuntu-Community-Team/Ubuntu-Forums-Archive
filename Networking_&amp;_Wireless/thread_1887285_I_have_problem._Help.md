---
title: "I have problem. Help"
date: 2011-11-26
forum: Networking &amp; Wireless
---

### Post by Michas1991 on 2011-11-26
I have installed Ubuntu 10.4 LTS on my pc and i can't connect to the internet. I live in an accomodation and the internet is with a wire and a can't connect. Can anyone help me?

---

### Post by squenson on 2011-11-26
Did you properly connect the cable?
Do you have another OS on this computer and does Internet work with this second OS?
Do you see any error message?
Could you open a command line window (Ctrl-Alt-T) and type the command ifconfig. Paste the result here.

---

### Post by Michas1991 on 2011-11-26
I have Windows and ubuntu side by side. I have the cable connected to my pc. Could you tell me what to do to have access to the internet with Ubuntu?

---

### Post by Michas1991 on 2011-11-26
These are the results:


christos@christos-laptop:~$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:28 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1680 (1.6 KB)  TX bytes:1680 (1.6 KB)

christos@christos-laptop:~$

---

### Post by squenson on 2011-11-27
May be [this thread]("http://ubuntuforums.org/showthread.php?t=1741686&highlight=create+eth+connection") could help.

---

### Post by Scott Baker on 2011-11-30
Howdy. If you don't mind, could you provide more info for the group. The make and model of the machine that you did your install on would help greatly. If you have the info for your network card, that would also help. Also, do you have ANY internet access on this machine at all? If so, have you installed all of the current "UPDATES" (not UPGRADES), for this version? Based on the little info you've provided, it sounds like you're having an issue with missing/incomplete network card drivers, but won't know until more info is provided. :roll:

---

