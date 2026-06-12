---
title: "Lost connections"
date: 2009-06-22
forum: Networking &amp; Wireless
---

### Post by Enk on 2009-06-22
I installed ubuntu 9.04 a month ago or so and have no problem with the network connections, but yesterday I suddently couldn't connect to my router. 

The "Wireless Network" is just grayed out. 

My girlfriends computer (running Windows) has no problems.

I tried connecting with a cable but the network icon just kept spinning around till I got the message "Wired Network Disconnected". 

I cannot connect to my router (192.168.0.1) from my laptop. 


I cannot remember performing any updates before the problem occured (tho I update quite automaticly so I really can't say if I did or not :P )

Thanks for any replies!

---

### Post by jonobr on 2009-06-22
Hello

Heres a couple of things to try.

Im assuming your doing dhcp, however, start here

run ifconfig in a terminal window,
see if that shows you have obtained an ip address from the router

if its empty try

sudo dhclient
and ifconfig again to see if you got anything.
POst back the results of both and see what heppens,

If its still causing trouble post back the contents of lshw

---

### Post by Iowan on 2009-06-22
I had a similar [problem]("http://ubuntuforums.org/showthread.php?t=1156441") (though it didn't take a month to occur). I'll include it for reference - though I doubt it's your solution.

---

### Post by Enk on 2009-06-23
Thanks Jonobr! 

dhclient did the trick *adding it to my handy tomboy notes*

---

### Post by jonobr on 2009-06-23
mmmm.... interesting,

its just glossing over your problem.

It appears the connection did not renew its lease correctly.

Whats supposed to happen in dhcp is the client says on boot time is,

here I am what IP address and gateway do I use,
the dhcp server (your router in this case)
says ok, heres you ip address, check back in a certain time (or keep it for this length of time).
It sounds as if you card losts its ip info, and did not ask for it again,
or did not renew its lease.

the command I gave you , just tells the card to reacquire from the dhcp server.
In the windows world its like doing an ipconfig /renew on your ethernet adaptor
So what I would do is, keep an eye on this and see how often it happens,
it may be just a one off, but now harm watching it.
Ciao

---

