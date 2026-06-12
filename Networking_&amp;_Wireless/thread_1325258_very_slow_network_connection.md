---
title: "very slow network connection"
date: 2009-11-13
forum: Networking &amp; Wireless
---

### Post by hoibat on 2009-11-13
hi there

im very new to ubuntu, so plz help me and learn me how to get my ubuntu to work

my problem:
i've got a HP 6710b Notebook
with a Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express Network card installed
i'm using the new ubuntu9.10

when i'm using my wireless link everthing seems ok, but as soon as i'm using my LAN connection my speed slows down so that working with it doesn't make fun..
i'm talking about 3-7kbit/s at maximum. back in winXP i'm running with 400-600 kbit/s!

i've allready checked the IPv6 issues, but disabling inet6 didn't bring any speed back..

everything else worked very well, and if this problem is solved im the newest ubuntu user! ;)

hope anyone can help me..

and sorry for my english, i'm swiss. :) so if theres a great german speaking user he can write back in german, would be easier for both of us. :D

thx to every answers

hoibat

---

### Post by Krause on 2009-11-13
try disabling the wireless on the laptop (should have some kind of hardware toggle switch) see if that helps.

Im thinking most the issues with the networking in 9.10 has to do with network manager screwing something up when more then 1 connection is present.

Ive found this to be the case when I have both network lines plugged in (my computer has 2 nic ports) to the switch, but when just 1 is plugged in (either one) it works flawless.

---

### Post by hoibat on 2009-11-16
hi krause

thx for your help, but at the moment my wifi is turned off... so, this can't be the problem.

i've also updated my LAN link driver but with no effect..

don't know what else i can try..!

just to let you all know how slow it is:
at the moment i'm downloading the vlc media player, which is about 5mb. it is to 25% downloaded and it took me about 1 hour...

hope i'll get this fixed..

---

### Post by hoibat on 2009-11-18
now it all changed.. :(
 
after spending some hours with my problem, my eth0 has gone.
 
after system update(which took abot 6h) and reboot, i cannot even use my nic.
 
with ifconfig the terminal shows all connections, but there is a new one: eth0:avahi
but with a 169... IP. and thats wrong.
 
same machine back in winXP works perfectly. So its not a DHCP problem, its not a DNS problem and also not a hardware failure.
 
have anyone had the same problems like me...????
 
thx4all answers!!

---

### Post by crucialhoax on 2009-11-18
I had a similar problem, I had a very fast connection in Vista but a 50kb/s connection in linux. I was using the default network manager that came with Karmic, I downloaded and installed Wicd. Since then my connection has been great!

[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

---

