---
title: "I have no idea where to start!"
date: 2009-08-27
forum: Networking &amp; Wireless
---

### Post by ozzman24 on 2009-08-27
First off, can't connect to the internet. 

Secondly, I not a retarded as most would think. 

What I've done so far is. I've right-clicked the network icon (to the left of the date & time but you guys prolly already know that), then clicked on "edit connections" and that brought me to the network connections window. The I clicked the DSL tab and continued to create a connection, entering my user name & password and thus creating a DSL connection. When I attempt to connect the DSL connection it always comes back saying connection disconnected.

I've used Ubuntu 8.10 before and had a similar trying to connect. Except I came across a simple command I was able to punch in the Terminal that made the connection work. In my opinion I need to do something to "activate" my network adapter. 

By the way it's an on board adapter, Gigabit ethernet adapter, on a Fatal1ty FP-IN9 board. Any suggestion guys?

---

### Post by Iowan on 2009-08-27
You can check **ifconfig -a** to see which connections have IP address. 
**lshw -C network** will provide a list of interfaces. My DSL modem handles all the PPPOE stuff - I just connect to it like a router.

---

### Post by ozzman24 on 2009-08-28
Okay I think I have found what I have been looking for here > [https://help.ubuntu.com/7.04/internet/C/connect-to-internet.html](https://help.ubuntu.com/7.04/internet/C/connect-to-internet.html) [[COLOR=Black][/COLOR]]("https://help.ubuntu.com/7.04/internet/C/connect-to-internet.html")

---

### Post by ozzman24 on 2009-08-28
Okay I didn't have to do anything. Plug in the DSL and it connected. Apparently it was as easy as it looked. Though now I am having trouble with installing plug-in's and what not. I don't think I am going to fully convert to any linux based OS any time soon.

---

### Post by Iowan on 2009-08-28
> **ozzman24 said:**
> Okay I didn't have to do anything. Plug in the DSL and it connected. Apparently it was as easy as it looked... I don't think I am going to fully convert to any linux based OS any time soon.Hmmm... too easy for you - not enough challenge? ;)

---

### Post by ozzman24 on 2009-08-30
Easy for ME? LOL, not hardly. Though I think I am making this Ubuntu this out to be harder than what it really is. Tell me, if you've fully converted to a Linux OS how do you manage without a Microsoft OS? Sure, Ubuntu has pretty much the same capabilities as any Windows OS but it seems to me that an Ubuntu user would have trouble "connecting" with a Windows user in a world where Windows software will always be available, and there are much more Windows users than Ubuntu users. 

So how did you guys make the switch and on a day to day basis cope with a Windows world? May be I don't fully understand how to get around the limitations of a Linux system in a Windows world. Any advice? Because although Windows is a great program, I don't like the idea of buying from a Nazi (Bill Gates)!

---

