---
title: "Wifi Problems!"
date: 2011-06-18
forum: Networking &amp; Wireless
---

### Post by TheCuomo on 2011-06-18
I too am having WiFi problems and maybe you have some wisdom for me?

I had 10.10, and all was well. Then I installed natty, and WiFi worked for a while, then stopped working.  I later went back to 10.10, and WiFi still isn't working.

The WiFi icon in the top bar looks like it's scanning. But it just keeps on scanning, continuously. Then it asks me for the password, so it obviously connects to something if it knows the network needs a password.

But here's the weird thing, my router also creates a BT Open Network, which I think is some pay service that BT offer, apparently through anyone's wifi since it's not password protected. I can connect to that.  But not the actual network that leads to the internet.

This happened a while back, and of course I can't install any updates on it because I can't get online. I am writing this from XP on the same computer, and XP can connect to the network no problem. 

What should I try next?  Thanks for any suggestions you might have!

---

### Post by TheCuomo on 2011-06-18
Praise be!

It's 10 hours since I posted the above and I've been working on this the whole time.  Feel like I wasted a day but at least the problem is solved.

I tried EVERYTHING, and 99% of the time I didn't have a clue what I was doing or what the things I was typing into the terminal meant. I even tried several different versions of linux in case that helped (actually typing this from a version of mint which I'll have to switch back to normal ubuntu... just had enough with installers for one day).

The problem:

Some kind of upgrade to BT's router software which rolled out in May sometime.

The solution:

Set a fixed IP by right clicking the wireless icon, going to "Edit Connections", clicking the right network, going to ipv4, then setting the following:

IP Address - 192.168.1.xx  (the last two can be any that aren't being used on the network already, just pick random numbers)
Net Mask 255.255.255.0 
Gateway - 192.168.1.254 
DNS Server - 192.168.1.254.

Then the wireless connects normally.  Hope this is useful to someone!

:popcorn:

---

