---
title: "I can not access to the Internet"
date: 2010-09-03
forum: Networking &amp; Wireless
---

### Post by na3no3 on 2010-09-03
[CENTER]Hello):P
Sorry Dear
I do not speak English:(
But I use the dictionary ^ _ ^:D
I have a problem in Ubuntu system
Which I can not access to the Internet: (
Note::redface:
I have a DSL
The view of a user name and password
I use the cable already in the System 7
But now the Internet does not work never what is the solution?
Please type modem
d-Link
Thanks:oops:[/CENTER]

---

### Post by BkkBonanza on 2010-09-03
You'll have to provide more information about your system and what you did. 
We aren't magicians and can't pull answers out of a hat without details.

Start with providing output from these commands,

ifconfig

cat /etc/networking/interfaces

---

### Post by na3no3 on 2010-09-03
> **BkkBonaza said:**
> You'll have to provide more information about your system and what you did. 
We aren't magicians and can't pull answers out of a hat without details.

Start with providing output from these commands,

ifconfig

cat /etc/networking/interfaces


OK
How can I give you information about the system?
Please, what is the way to take the information system?:(

---

### Post by BkkBonanza on 2010-09-03
Go to the menu and select Applications, Accessories, Terminal. This will open a terminal on your system. Type in the commands above. Select, copy and paste the output into a post here. This info will help us know how your system is configured and if something is wrong.

---

### Post by na3no3 on 2010-09-03
[CENTER]free-user@free-user:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:a0:24:a9:08:b3  
          inet6 addr: fe80::2a0:24ff:fea9:8b3/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:40 errors:0 dropped:0 overruns:0 frame:0
          TX packets:25 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2400 (2.4 KB)  TX bytes:1716 (1.7 KB)
          Interrupt:22 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:******  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4272 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4272 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:439837 (439.8 KB)  TX bytes:439837 (439.8 KB)

free-user@free-user:~$ 

will be back
[/CENTER]

---

### Post by BkkBonanza on 2010-09-03
Please do not post text centered. It's very hard to read.

Your output indicates you have an interface eth0 that is not brought up yet.
Try this command,
[B]
sudo ifconfig eth0 up[/B]

and post output. This should have been brought up during booting but there may be some reason why it wasn't. Your other config files may show why.

---

### Post by na3no3 on 2010-09-03
> **BkkBonaza said:**
> Please do not post text centered. It's very hard to read.

Your output indicates you have an interface eth0 that is not brought up yet.
Try this command,
[B]
sudo ifconfig eth0 up[/B]

and post output. This should have been brought up during booting but there may be some reason why it wasn't. Your other config files may show why.


sorry my friend i can"t spake english will:(

free-user@free-user:~$ ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:a0:24:a9:08:b3  
          inet6 addr: fe80::2a0:24ff:fea9:8b3/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:40 errors:0 dropped:0 overruns:0 frame:0
          TX packets:25 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2400 (2.4 KB)  TX bytes:1716 (1.7 KB)
          Interrupt:22 Base address:0x4000 

free-user@free-user:~$

---

### Post by na3no3 on 2010-09-03
> **BkkBonaza said:**
> Please do not post text centered. It's very hard to read.

Your output indicates you have an interface eth0 that is not brought up yet.
Try this command,
[B]
sudo ifconfig eth0 up[/B]

and post output. This should have been brought up during booting but there may be some reason why it wasn't. Your other config files may show why.


I've written which thou hast given him You

But there is a problem

When it appears enter the password

Keyboards are not able to enter the numbers Why?

I do not know what the problem:(

---

### Post by lisati on 2010-09-03
> **na3no3 said:**
> I've written which thou hast given him You

But there is a problem

When it appears enter the password

Keyboards are not able to enter the numbers Why?

I do not know what the problem:(

When you put in your password for something using "sudo", it won't show on the screen. Just type it as usual.

(By the way, most English speakers I know don't use "thee", "thou" etc. and the corresponding verb forms these days unless they are trying to be clever or to sound spiritual.)

---

### Post by na3no3 on 2010-09-03
> **lisati said:**
> When you put in your password for something using "sudo", it won't show on the screen. Just type it as usual.

(By the way, most English speakers I know don't use "thee", "thou" etc. and the corresponding verb forms these days unless they are trying to be clever or to sound spiritual.)

OK
After that?

I wrote the password then what?

Because there was no change

---

### Post by BkkBonanza on 2010-09-03
Now show us output from **ifconfig** command again.

---

### Post by na3no3 on 2010-09-03
> **BkkBonaza said:**
> Now show us output from **ifconfig** command again.

I think
Like the former:(

free-user@free-user:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:a0:24:a9:08:b3  
          inet6 addr: fe80::2a0:24ff:fea9:8b3/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:40 errors:0 dropped:0 overruns:0 frame:0
          TX packets:25 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2400 (2.4 KB)  TX bytes:1716 (1.7 KB)
          Interrupt:22 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:***.*.*.*  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:10303 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10303 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1021050 (1.0 MB)  TX bytes:1021050 (1.0 MB)

free-user@free-use

---

### Post by na3no3 on 2010-09-03
[CENTER][FONT=Franklin Gothic Medium][SIZE=6]up[/SIZE][/FONT]
[/CENTER]

---

### Post by BkkBonanza on 2010-09-03
Well, for some reason you are not getting an address assigned. You should be getting an address on your local LAN in that output. This is strange because it indicates the link is UP. Are you removing anything from that output?

Do you know your gateway address? If so, then you should be able to ping that address.

The answer may be in the **cat /etc/networking/interfaces** output you still did not post.

---

### Post by na3no3 on 2010-09-03
> **BkkBonaza said:**
> Well, for some reason you are not getting an address assigned. You should be getting an address on your local LAN in that output. This is strange because it indicates the link is UP. Are you removing anything from that output?

Do you know your gateway address? If so, then you should be able to ping that address.

The answer may be in the **cat /etc/networking/interfaces** output you still did not post.


> 
The answer may be in the cat /etc/networking/interfaces output you still did not post.

Brother Can you explain what is borrowed?.

Because I really did not understand much:(

---

