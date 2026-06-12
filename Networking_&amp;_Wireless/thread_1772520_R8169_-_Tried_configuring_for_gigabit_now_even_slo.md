---
title: "R8169 - Tried configuring for gigabit now even slower than before"
date: 2011-05-31
forum: Networking &amp; Wireless
---

### Post by Error07 on 2011-05-31
This is a strange problem that I have read many people having:

I was getting full gigabit speeds when sending files TO my linux box, but when pulling them FROM the linux box my speeds capped out at ~16MB/s. 

I tried a lot of things and none have worked and now I am in a worse situation having downloaded the drivers straight from realtek; now I can barely pull 6MB/s either way. 

How do I rid the drivers from realtek and go back to whatever drivers linux used on its own when I first installed the card? 

I have tried ethtool to set the gig speeds and even though it reads supported and advertised, when set to 1000 (ethtool -s eth0 speed 1000 duplex full autoneg on) then doing /etc/init/d/networkin restart it still shows 100Mb/s with the ethtool eth0 command. 


Any help is GREATLY appreciated, even if I cant solve the original problem id like to get back to at least having gig speeds one way! 

Thanks.


edit: Now I dont know whats going on.. I have local network access but I am not getting anywhere outside the lan "no route to host".

---

### Post by Error07 on 2011-05-31
now I got things all screwy, got my external net back by adding a nameserver in /etc/resolv.conf but now ping is like 15ms to google and I cant get a speed test reading over 5mb on the computer! 

I removed all the routes except the one I set in resolv.conf so it shows:

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.2.10    0.0.0.0         UG    100    0        0 eth0

but when I do networking restart I get: 

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.2.0    0.0.0.0           255.255.255.0  U      0        0       0   eth0
169.254.0.0    0.0.0.0           255.255.0.0      U      1000  0       0   eth0
0.0.0.0           192.168.2.10  0.0.0.0             UG    100    0       0   eth0

and still have a really high ping.... whats going on here???

---

### Post by Error07 on 2011-06-01
Okay everything is back to normal as far as my lan/wan connections and ping, only problem left is getting my gig speeds back. 

No matter what when I set them via ethtool they go back to what they were previously. I read this was a bug in an older kernal but was supposed to have been resolved yet here I am having the problem.

Guessing nobody has the answer maybe I will just try a new gigabit card and do some research on its linux compatibility first.

---

### Post by ian dobson on 2011-06-01
Hi,

The R8169 is known to be a slow network card (even under windows). I have one in my HTPC and in the end I just installed a Intel network card and disable the onboard card.

Regards
Ian Dobson

---

### Post by Error07 on 2011-06-01
I dont mind it being slow - I just want it to get back to the speeds I was getting. As for now its stuck in 100mb mode, at least before I was getting 35MB to the computer and 16MB from it.

---

