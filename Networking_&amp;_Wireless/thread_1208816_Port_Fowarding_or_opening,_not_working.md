---
title: "Port Fowarding or opening, not working"
date: 2009-07-09
forum: Networking &amp; Wireless
---

### Post by kernel89 on 2009-07-09
This was my process, please point out the errors I might have done.
Thank You.

First I set up a Static IP on the Network Connections option.
[IMG]http://i30.tinypic.com/29wqy3t.png[/IMG]

Then I set up a port for Transmission.
[IMG]http://i31.tinypic.com/2mx3onm.png[/IMG]

Then I added that to my router preferences.
[IMG]http://i32.tinypic.com/2r3dzep.png[/IMG]

Lastly, when I checked to see if my ports really were open, I tested it, and failed.
[IMG]http://i26.tinypic.com/x5bodt.png[/IMG]

The reason why I want to forward my ports is because ever since I switched to Ubuntu 9, my internet keeps disconnecting when I run Transmission.

I'll try this port forwarding method, if my connection keeps getting interrupted, I might as well switch to Ktorrent.

---

### Post by ddivney on 2009-07-16
Any luck man? I'm stuck on the same deal... I'll let you know if I find anything

---

### Post by cariboo on 2009-07-16
To check if the ports are open from the outside go to [canyouseeme]("http://canyouseeme.org/").

---

### Post by superprash2003 on 2009-07-17
post output of **sudo iptables -L **, do you have firestarter or anything similar running?

---

### Post by Tofu_Madness on 2009-08-29
Much like what kernel89 was describing, I got a static ip through the Network Manager and opened a port in my router firewall/virtual server for Transmission to use, but when I checked the Transmission's preferences port was always **closed**.. 

Well, after bit of messing around enabling UPnP on my router fixed the problem. I really don't understand the difference between UPnP and the manual setup, because the firewall/virtual server has exactly the same setting as before... Oh, I did had to restore my router to the factory setting, because I was having trouble loging in. Maybe that was the trick? :confused:

I don't know. The port is freaking open and I am happy. :guitar:

---

