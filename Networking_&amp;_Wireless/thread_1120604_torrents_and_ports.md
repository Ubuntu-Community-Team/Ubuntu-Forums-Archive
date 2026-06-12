---
title: "torrents and ports"
date: 2009-04-09
forum: Networking &amp; Wireless
---

### Post by sway.jd on 2009-04-09
hello, I almost fully switched to ubuntu but there is this little thing bugging me.

whatever bittorrent client I use i always get the felling that the port i choose is never properly opened. when in fact it is.

i'm behind a switch and I have a static ip on my pc set to 192.168.1.136 and i have the port 2xxxx (dont know if it is safe to tell) opened to that ip on my switch.

so i set that same port on the client but in fact it never is opened.

this is a problem with ubuntu cause in windows it works just fine.


can you guys give me a hand? maybe i set the static ip wrong or something...

oh btw, I'm no expert, not even close. so i would apreciate greatly if you could explain things thoroughly. you know, newb talk.

thanks!

---

### Post by superprash2003 on 2009-04-09
by default , it should allow.. unless you are running firestarter or ufw??try this online port scanner to see if port is open [http://www.t1shopper.com/tools/port-scanner/](http://www.t1shopper.com/tools/port-scanner/)

---

### Post by sway.jd on 2009-04-09
no. no firewall whatsoever. it says the port doesn't respond. i tried a scanner like this before and the result was the same, then i switched to my windows installation and the same website said the port was open.

---

### Post by sway.jd on 2009-04-10
actually i just tried the port scanner website and the result is the same, no response.

but when i use the embuted port scanner that uTorrent comes. the result is OK. port opened.

in windows of course.

---

### Post by superprash2003 on 2009-04-10
could you post the screenshot of the port forwarding page on your router.. and output of **ifconfig** from the terminal of ubuntu

---

