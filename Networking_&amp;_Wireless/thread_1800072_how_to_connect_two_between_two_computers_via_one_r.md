---
title: "how to connect two between two computers via one router"
date: 2011-07-08
forum: Networking &amp; Wireless
---

### Post by hanansela on 2011-07-08
HI all 
I have two Ubuntu 11.04 machines connected via cable to the same D link ADSL router. how do i connect one to the other so i can see  from the other computer files and transfer them using nautilus?   
thank you

---

### Post by josephmills on 2011-07-08
use vnc and ssh on top of that set up you network hope that this helps 
[https://help.ubuntu.com/8.04/internet/C/networking-shares.html](https://help.ubuntu.com/8.04/internet/C/networking-shares.html)

---

### Post by hanansela on 2011-07-08
Thank you for the advise but I need more details. Maybe some things seems obvious but i need the basics, step by step. How does one computer recognize the other via SSH? when both of the computers are connected to the same router. typing SSH "computer_name" leads nowhere. They both have the same ip address.
Thank you

---

### Post by Iowan on 2011-07-08
> **hanansela said:**
> They both have the same ip address.That shouldn't work...
Are you talking about an external IP address?

---

### Post by hanansela on 2011-07-09
Yes, I figured out that i can not use the external  IP adress in ssh. What should i use instead? how can i find the local address? is there any configuration or software to use to get this connection?

---

### Post by spiky001 on 2011-07-09
If you open a terminal on each pc type ```
ifconfig
```that will give you the ip address on the computor

---

### Post by hanansela on 2011-07-09
OK i run ifconfig and got this:
> eth0      Link encap:Ethernet  HWaddr e0:69:95:9a:a4:b6  
          inet addr:10.0.0.1  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::e269:95ff:fe9a:a4b6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5468 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5269 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4040590 (4.0 MB)  TX bytes:1051123 (1.0 MB)
          Interrupt:20 Memory:fe400000-fe420000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:64 errors:0 dropped:0 overruns:0 frame:0
          TX packets:64 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5472 (5.4 KB)  TX bytes:5472 (5.4 KB)I have tried to connect from the other computer using  inet addr 10.0.0.1 and I got:
 > port:22 connection refused

---

### Post by spiky001 on 2011-07-09
ok do you have ssh server installed on the pc? and what is ip of other machine?

---

### Post by hanansela on 2011-07-09
As I said before, I knew it was something obvious (but not to me). I have installed ssh server on the remote computer  and now i can connect.
Thank you

---

### Post by timstott on 2011-07-09
Hello hanansela,

If I understand correctly you have two computers (A and B) connected to the same router. You can view remotely B from A, and so far you don't seem to be able to connect to B via ssh?

Have you installed ssh on the host computer B?

In terminal:

```
sudo apt-get install openssh-server
```

[_Here_]("http://www.cyberciti.biz/faq/ubuntu-linux-openssh-server-installation-and-configuration/") is more on how to install it if this is not sufficient.


Just to make sure nothing is wrong with the network, try to ping the host from the client (B from A)

In terminal:

```
ping the.server.ip.adress
```

You should be getting a response in ms and not a time out.

---

### Post by hanansela on 2011-07-09
Thank you [timstott]("http://ubuntuforums.org/member.php?u=1224457") for the detailed replay - I have already installed ssh server after [spiky001]("http://ubuntuforums.org/member.php?u=915355") quetion about it, everything runs OK.  My initial problem was that I assumed that if I have ssh client I also have ssh server.

---

