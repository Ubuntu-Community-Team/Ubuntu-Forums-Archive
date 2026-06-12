---
title: "OpenVPN, Ssh, blocked ports and campus firewall, need some advice."
date: 2009-03-25
forum: Networking &amp; Wireless
---

### Post by MajorTom00 on 2009-03-25
Hey there,

I've been all over these boards for the last day and a half, and 
crawling across the slew of Google, but still haven't found someone
with a solution to a close enough problem to solve mine.

Currently, I'm on my college campus. There is a ridiculous firewall 
that blocks pretty much everything, for example, I can browse web 
pages, and go on msn(on my windows machine) but cant send or receive 
files, FTP works fine too. 

Now, all this wasn't a problem because the school has some mad 
connection, at the start of the year I was getting download speeds 
around 2 megabytes/s. however, since the launch of Confiker(?) the 
school has been scanning its network around the clock, now my 
connection is worse than old dialup.

I had been using a proxifier and Your Freedom to get around the 
firewall to play games, get around restricted areas and so on, but 
lately the connection is so bad there's no point.

Even if this doesn't speed my connection, It's still something I'd
like to do, as a future alternative to Your Freedom. Plus, having
a connection to the home network means network storage. :D

I've made a diagram of what I want to do:
[IMG]http://photos-h.ll.facebook.com/photos-ll-snc1/v2684/22/80/872700281/n872700281_6284199_1757375.jpg[/IMG]

The things I would like to know are as follows:

1. My Ubuntu box at home will receive a naked internet connection from 
the modem through it's Eth0, how do I share that connection through 
Eth1 to the router and rest of the network? What is this called?

2. What ports can an SSH terminal run on? This would just be for 
instruction and configuring the box. My school blocks most ports, save 
for 80, 443, and whatever ftp uses, whereas my ISP at home specifically 
blocks incoming port 80, 22 and most other to hinder people (like me) 
who try and set up servers on their home connection.

3. I've followed the HOWTO on OpenVPN and with my linux prowess could 
probably figure it out (I'm still pretty new), but this is more of a 
port issue. I'd have to be able to tunnel all my VPN traffic through 
port 80, or rather a port that isn't blocked by my school's firewall, 
or my ISP, I'm curious if there's any ports VPN can't run on. I want to 
set this network up as a bridge.

I think that's all the information I can supply. Any helpful advice or instruction would be greatly appreciated.

Thanks.

---

