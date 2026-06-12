---
title: "PPPOE cant run"
date: 2011-07-16
forum: Networking &amp; Wireless
---

### Post by fernado on 2011-07-16
I use win7 bit and input the ISP username and password, it runs well,
but after I swap system to Ubuntu 11.04 64bit, I cant use the username and password to run DSL successfully.

I use the
[PHP]
sudo pppoeconf
[/PHP]
A text-based menu program will guide you through the next steps, which are: 

[LIST=1]
[*]Confirm that your Ethernet card is detected. 
[*]Enter your username (provided by your ISP). 
[*]Enter your password (provided by your ISP). 
[*]If you already have a PPPoE Connection configured, you will be asked if it may be modified. 
[*]Popular options: you are asked if you want the 'noauth' and 'defaultroute' options and to remove 'nodetach' - choose "Yes". 
[*]Use peer DNS - choose "Yes". 
[*]Limited MSS problem - choose "Yes". 
[*]When  you are asked if you want to connect at start up, you will probably  want to say yes. (This option does not work) See the secton "Connecting  on Boot" 
[*]Finally you are asked if you want to establish the connection immediately. 
[/LIST]
Once you have finished these steps, your connection should be working. 

after that 
when I type plog, it shows below error
[PHP]
Jul 15 21:57:42 ubuntu pppd[2425]: pppd 2.4.5 started by root, uid 0
Jul 15 21:57:42 ubuntu pppd[2425]: PPP session is 13825
Jul 15 21:57:42 ubuntu pppd[2425]: Connected to 80:81:00:5d:b2:11 via interface eth0
Jul 15 21:57:42 ubuntu pppd[2425]: Using interface ppp0
Jul 15 21:57:42 ubuntu pppd[2425]: Connect: ppp0 <--> eth0
Jul 15 21:57:42 ubuntu pppd[2425]: appear to have received our own echo-reply!
Jul 15 21:57:42 ubuntu pppd[2425]: Remote message: not user
Jul 15 21:57:42 ubuntu pppd[2425]: PAP authentication failed
[/PHP]
:(

---

### Post by fernado on 2011-07-16
Do u know the reason? I just cant use the DSL to connect to the Internet.

even I use the Graphic configuration "Edit Connection" also cant.

---

