---
title: "Internet connection through another computer"
date: 2010-11-17
forum: Networking &amp; Wireless
---

### Post by LorraineO on 2010-11-17
I have a computer running XP with a wireless internet connection. I have installed Ubuntu 10.04 on a second computer. I would like to connect my Ubuntu computer to the internet through a wired connection to the XP computer. As I am a newby to Linux commands could someone explain how to do this in laymans terms.

Lorraine

---

### Post by spiky001 on 2010-11-17
You will need a **Cross over** ethernet cable OR a **hub** which you can connect an ordinary ethernet cable

---

### Post by LorraineO on 2010-11-17
I have an ethernet cable Just need to know how to set it all up software wise.

---

### Post by spiky001 on 2010-11-17
It,s not the normal eth0 cable it needs to be a crossover,  [http://en.wikipedia.org/wiki/Ethernet_crossover_cable](http://en.wikipedia.org/wiki/Ethernet_crossover_cable)  unless you have a hub/switch or router

---

### Post by stefangr1 on 2010-11-17
> **spiky001 said:**
> It,s not the normal eth0 cable it needs to be a crossover,  [http://en.wikipedia.org/wiki/Ethernet_crossover_cable](http://en.wikipedia.org/wiki/Ethernet_crossover_cable)  unless you have a hub/switch or router

On most systems a crossover cable is no longer needed. You may need to do some configuration on both systems though, unless there's a feature to do this that I'm not aware off.

OK, until very recent, this would have been quite difficult as you would need to enable routing by the kernel, manually configure your network, and add a default route to your routing table. With Ubuntu 9.10, however, this has changed completely, and you can share your connection with just a few clicks, as is pointed out in [tutorial](http://www.highqualityinternetcorn.com/?page=Article&id=6).

---

### Post by LorraineO on 2010-11-17
The wi fi is on a Windows computer

---

### Post by stefangr1 on 2010-11-17
> **LorraineO said:**
> The wi fi is on a Windows computer

I edited my post above. It doesn't matter what operating system the other system is using.

---

### Post by phoenixpb on 2010-11-17
just connect the linux computer to windows computer
install the software 
**NetCom 1.3**

Publisher: NetCom

in the windows computer
that's all

:)

---

### Post by peyman on 2010-11-17
After you physically connected your two machines assign an IP address to each machine so the can ping each other. I assume you assign 192.168.0.1/255.255.255.252 on your Lindows host and 192.168.0.2/255.255.255.252 on your Linux host. Now set your Linux box default gateway to be 192.168.0.1 and go to your windows box and right-click on the Internet connection and share it. That is it.

---

### Post by ThatGuy5 on 2011-01-07
If you want to ensure fast networking speeds, make sure you use [Cat 6 Cable]("http://www.computercablestore.com/c_cat6_bulk_cable.aspx")

---

### Post by ThatGuy5 on 2011-01-07
If you want to ensure fast networking speeds, make sure you use [Cat 6 Cable]("http://www.computercablestore.com/c_cat6_bulk_cable.aspx")

---

### Post by ThatGuy5 on 2011-01-07
If you want to ensure fast networking speeds, make sure you use [Cat 6 Cable]("http://www.computercablestore.com/c_cat6_bulk_cable.aspx")

---

### Post by ThatGuy5 on 2011-01-07
If you want to ensure fast networking speeds, make sure you use [Cat 6 Cable]("http://www.computercablestore.com/c_cat6_bulk_cable.aspx")

---

