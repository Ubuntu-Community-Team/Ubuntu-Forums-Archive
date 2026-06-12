---
title: "Help! New to Ubuntu and can't connect to my network"
date: 2008-12-22
forum: Networking &amp; Wireless
---

### Post by slh92027 on 2008-12-22
I'm very new to Ubuntu and not very computer savvy.  I just received a new Dell Inspiron 910 pre-installed with Ubuntu and can't get it to connect my network.  It recognizes it on the list of available networks and after entering the passcode, it still won't connect.  I've been searching for answers for 2 days now and am getting frustrated.  What do I need to do to get this to work?  Can anyone help?  Thanks.

---

### Post by jonobr on 2008-12-22
hello


go to a terminal window and post the results of lshw and ifconfig to see whats what.

---

### Post by slh92027 on 2008-12-22
As you'll see below it won't let me enter a password.

scott@scott:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:21:70:d2:80:13  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:3732609449 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:220 Base address:0xa000 


eth1      Link encap:Ethernet  HWaddr 00:23:08:39:ba:ca  
          inet addr:192.168.0.14  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::223:8ff:fe39:baca/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:27748 errors:0 dropped:0 overruns:0 frame:29957
          TX packets:15116 errors:1 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:41489982 (39.5 MB)  TX bytes:1141209 (1.0 MB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1434 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1434 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:71700 (70.0 KB)  TX bytes:71700 (70.0 KB)


scott@scott:~$ sudo lshw
[sudo] password for scott: 

Sorry, try again.
[sudo] password for scott:

---

### Post by Iowan on 2008-12-22
Sorry to bombard you with questions, but...
Did laptop come with Live disk? 
Did you use the same password you use to log on to machine?
Do you *need* a login password (or was it set up without one)?
[Here]("Here") is a link for resetting password - although that's not what you asked about.

---

### Post by slh92027 on 2008-12-22
Yes, it came with a live disk, if you mean the OS disk.
I don't need password to log in, just to make changes.

---

### Post by jonobr on 2008-12-22
To expand on Iowans point,
you need to ahve a password on there,
if you dont need one to log in, Im guessing if you run sudo lshw and enter no password it will work.

Any which way, I see you have two ethernet connections and the second one is now connected.
Ping your own address....

ping 192.168.0.14

assuming the router you have is 192.168.0.1
ping 192.168.0.1

then see you can reach a dns
type 

nslookup google.com

see what the response is like,
post any errors back here.

Use the IP address returned (if any) to go to google.

eg in firefox enter 74.125.45.100


let us know how that goes

---

### Post by Iowan on 2008-12-22
> **jonobr said:**
> ...if you dont need one to log in, Im guessing if you run sudo lshw and enter no password it will work. That's kinda where I was going - if you don't need one to log in, you probably don't need one to **sudo**.  If it asks for one, just hit [ENTER].
I'm a bit curious about eth0 - dropped:3732609449???
BTW, on my machine **lshw** runs without **sudo** - it complains, but runs.

---

