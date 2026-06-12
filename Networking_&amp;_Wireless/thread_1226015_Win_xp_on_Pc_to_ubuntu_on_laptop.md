---
title: "Win xp on Pc to ubuntu on laptop"
date: 2009-07-29
forum: Networking &amp; Wireless
---

### Post by charkoal on 2009-07-29
I need some help connection my laptop up to the pc via lan cable. I have it connected but then theres a message saying on the pc that there is limited or no connection, but on the laptop it shows that its connected.

my pc is connected to the internet on dial up so thats why i need to connect my laptop to my pc

---

### Post by superprash2003 on 2009-07-29
did you try setting up static ip on both machines?
machine 1 - ip = 192.168.0.1
machine 2 - ip = 192.168.0.2 and gateway = 192.168.0.1

---

### Post by Iowan on 2009-07-29
Depending on network card(s), you may need a crossover cable to connect between the two machines.

---

### Post by charkoal on 2009-07-29
> did you try setting up static ip on both machines?
machine 1 - ip = 192.168.0.1
machine 2 - ip = 192.168.0.2 and gateway = 192.168.0.1 

I did that thanks but its still not working.

I have a crossover cable and thats not the problem.

---

### Post by charkoal on 2009-07-29
The 2 computers in the corner of the screen show that its connected but they arent blue they are turned off, if this ifo helps anyone.


I disconnected the cable and reconnected then only the hosts computer icon turned on but not the second.

---

### Post by charkoal on 2009-07-29
In the networks connection on the pc it says the lan is connected, but yet I still cant get on the net on the laptop.

---

### Post by madmax1735 on 2009-07-29
hey, i would assume the you have two network interfaces (cards) installed on the pc running xp.

now a very easy way of going around this would be to share internet using ICS (internet connection sharing) on the xp machine and configuring the ubuntu to use dhcp on the Ethernet interface (eth0, usually)


also if u dont have a switch in between the two computers you would need a cross-cable.

---

### Post by charkoal on 2009-07-29
> now a very easy way of going around this would be to share internet using ICS (internet connection sharing) on the xp machine and configuring the ubuntu to use dhcp on the Ethernet interface (eth0, usually)

Can you please explain how to do this?

---

