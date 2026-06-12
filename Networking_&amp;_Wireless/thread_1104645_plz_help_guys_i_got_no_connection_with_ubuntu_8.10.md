---
title: "plz help guys i got no connection with ubuntu 8.10"
date: 2009-03-23
forum: Networking &amp; Wireless
---

### Post by rebrov on 2009-03-23
i just installed ubuntu 8.10 with xp os i got net connection in xp 

but no connection with ubuntu why ?

im user in Lan regular user i always make my ip and dns on xp 

obtain automatic 

but in Ubuntu i didn't touch anything i want to make it obtain automatic configuration to get connection like in xp !! how can i do that ,,,and btw when i see the connection place at desktop it say connection disabled with red triangle :S plz help

---

### Post by orethrius on 2009-03-23
Not enough information, please allow me to expand with a few follow-up questions.

1. What is the make and model (for instance, Gateway 450ZX or HP Pavilion 8210us) of your system?
2. Is it a laptop or desktop / tower?
3. Are you trying to connect over a wired or wireless connection?

From your initial report, it sounds like you're trying to connect a laptop via wireless with no success; without further information as above, troubleshooting the situation will be rather like testing lab rodents without ever examining them. ;)

EDIT: Before anyone takes offense, I am - of course - referring to the system as the lab rodent, not the user.  :-D

---

### Post by rebrov on 2009-03-23
> **orethrius said:**
> Not enough information, please allow me to expand with a few follow-up questions.

1. What is the make and model (for instance, Gateway 450ZX or HP Pavilion 8210us) of your system?
2. Is it a laptop or desktop / tower?
3. Are you trying to connect over a wired or wireless connection?

From your initial report, it sounds like you're trying to connect a laptop via wireless with no success; without further information as above, troubleshooting the situation will be rather like testing lab rodents without ever examining them. ;)

EDIT: Before anyone takes offense, I am - of course - referring to the system as the lab rodent, not the user.  :-D


hey bro 1- im just Lan user im trying to get connecting with my Lan server 
2- im a pc user not labtop

3-i didn't try to connect over wired nor wireless i tried over dsl

[http://img9.imageshack.us/img9/7058/11100023.png](http://img9.imageshack.us/img9/7058/11100023.png)

[http://img9.imageshack.us/img9/7688/85156150.png](http://img9.imageshack.us/img9/7688/85156150.png)

[http://img9.imageshack.us/img9/1014/13766844.png](http://img9.imageshack.us/img9/1014/13766844.png)

[http://img9.imageshack.us/img9/4325/70990333.png](http://img9.imageshack.us/img9/4325/70990333.png)

check the pics out plz

---

### Post by BkkBonanza on 2009-03-23
How are you connecting dsl to your pc? 

Usually dsl will connect to your dsl modem and then you would use ethernet (lan) to your pc from there. 

If that is the case (which is typical) then you do not configure PPP on your pc but you configure your lan (ethernet). In other words from your photos given you should not be configuring DSL or PPP but the "wired" connection. Your PC talks via LAN to modem and modem talks to dsl. If this isn't your config then please provide info about how your hardware is connected as a starting point.

---

### Post by rebrov on 2009-03-24
> **BkkBonaza said:**
> How are you connecting dsl to your pc? 

Usually dsl will connect to your dsl modem and then you would use ethernet (lan) to your pc from there. 

If that is the case (which is typical) then you do not configure PPP on your pc but you configure your lan (ethernet). In other words from your photos given you should not be configuring DSL or PPP but the "wired" connection. Your PC talks via LAN to modem and modem talks to dsl. If this isn't your config then please provide info about how your hardware is connected as a starting point.


look bro i connect via Lan i dont have modem or router or anything

the master pc of the server got it im just regular user in Lan so what im supose to do to make my connection stable the crazy thing that when i enter auto eth0 in terminal it doesn't recoginze auto as command why ?

i tried alot of commands to make my configuration auto but terminal doesn't recognize anything dunno maybe its just recognize some commands but not this commands about the internet connection

---

### Post by rebrov on 2009-03-24
check this commands out 

[http://img5.imageshack.us/img5/3909/30148127.jpg](http://img5.imageshack.us/img5/3909/30148127.jpg)

---

### Post by BkkBonanza on 2009-03-24
type: 
ifconfig -a
and paste results here

If you are on a lan then there is a router somewhere that gets you out to the net. You will need to know that router's ip to enter as your "gateway". But first, your results of above.

"auto eth0" is not a command for the console - it will need to be put into a config file used by network manager. But network manager will do that part for you if you use it.

---

### Post by rebrov on 2009-03-24
> **BkkBonaza said:**
> type: 
ifconfig -a
and paste results here

If you are on a lan then there is a router somewhere that gets you out to the net. You will need to know that router's ip to enter as your "gateway". But first, your results of above.

"auto eth0" is not a command for the console - it will need to be put into a config file used by network manager. But network manager will do that part for you if you use it.

ok i will and paste the result here gimme 10 min

---

### Post by orethrius on 2009-03-24
Wait, are you trying to say that you're sharing a local network, with no external Internet connection?  That's an entirely different kettle of fish.

---

