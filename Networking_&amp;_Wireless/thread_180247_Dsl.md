---
title: "Dsl"
date: 2006-05-21
forum: Networking &amp; Wireless
---

### Post by otis79 on 2006-05-21
I have a problem with a DSL connection. I use Ubuntu and I want to connect DSL modem directly to ethernet card. I tried to use RP-PPPoE and pppoeconfig. Nothing works. Pppoeconfig finds my eth0 and asks for user name and password but it can't connect. My modem is connected correctly :)
Please for advice
Thomas

---

### Post by RRS on 2006-05-21
Try this: 
System>Administration>Networking
Select eth0>properties>configuration>DHCP 

Often the DSL modem will handle the PPPoE and then provide DHCP service to your computer.

Do you also have Windows on this machine? If so, do you have to manually log-in to your ISP or is it automatic?

---

### Post by otis79 on 2006-05-22
I have only Ubuntu on my mashine. Eth0 is set up to use DHCP. I run  pppoeconf. After all it said all should be working ok. Funny thing is that when I run commad "poof", it says "No pppd is running.  None stopped"

---

### Post by yourearthlymaster on 2006-05-22
Hi, I'm new here.  But I have come across a similar problem.  
Does your DSL modem show an internet connection?  My system is showing a connection, but when I try to access the internet all I get is a popup that says the connection is being refused.  
If you get yours to work, let me know how (I'd do the same for you).

---

