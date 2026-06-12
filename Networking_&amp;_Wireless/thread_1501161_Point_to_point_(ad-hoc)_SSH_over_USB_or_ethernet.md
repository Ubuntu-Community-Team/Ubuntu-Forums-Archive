---
title: "Point to point (ad-hoc) SSH over USB or ethernet??"
date: 2010-06-03
forum: Networking &amp; Wireless
---

### Post by never gonna give you up on 2010-06-03
Hello,

I was wondering if there is any way to SSH from one computer to another and completely bypass a router or any other network infrastructure.

The reason I ask is because my robot ( same one in  [this post]("http://ubuntuforums.org/showthread.php?p=9407613#post9407613") ) often needs to change which wireless network it automatically connects to, however it is getting annoying to have to drag out a monitor and plug it in along with a keyboard and mouse every time this needs to happen. Instead I'd much rather just plug my laptop into the other computer, SSH in and change the network myself.

So I thought I would ask you kind people if this is possible. The  robot's computer has unused ethernet and USB ports, and I'd like to use those if at all possible (and with linux, anything is possible! -- sorta). I thought about doing something with ad-hoc, but this would limit my range (in infrastructure mode I can control the thing anywhere there is internet), and is to be avoided.

Thanks for your help!

---

### Post by psymeg on 2010-06-06
As long as the PC or laptop interface you wish to connect from has an IP address and netmask (eg IP address 192.168.1.10 netmask 255.255.255.0) in the same range as the robot you are connecting to, plugging in an ethernet cable should work. Note, if it is an older ethernet port it may not be auto sensing, and then you would need a crossover ethernet cable. 

[http://en.wikipedia.org/wiki/Ethernet_crossover_cable]("http://en.wikipedia.org/wiki/Ethernet_crossover_cable")

:guitar:

---

