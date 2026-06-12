---
title: "Question about Subsonic media server, statip IP, etc"
date: 2011-11-06
forum: Networking &amp; Wireless
---

### Post by boulezfan317 on 2011-11-06
Hello, 

I have just installed subsonic on my desktop which is running 11.04. 

I have been enjoying the heck out of streaming my music collection anywhere in my house (to android, roku, other computers) and everything seems to work flawlessly except that I cannot figure out how to access the server from OUTSIDE my wireless network. Here is what I've tried so far: 

First things first, the settings page in the browser interface for subsonic tells me that I am successfully forwarding port 4040. I also donated and thus have the ability to register a web address, which I have done - but status tells me that it is "registered but could not connect to it (connect timeout exception)" 
Also, I have assigned my desktop ethernet card a static IP address by editing etc/network/interfaces. ifconfig tells me my eth0 inet address is the new one I created.

The funny thing is, when I go to my router config page, there is a list of the machines on the network (its called dhcp client list) and my desktop still has the old ip address. I manually forwarded ports 4040 and 80 following the instructions on portforward.com, but canyouseeme.org still tells me that it can't see service on those ports. 

When I type in my new static IP address:4040 in the address bar of a browser I get to the subsonic login page and it works beautifully. 
I'm clearly connected to the internet, so I assume DNS names and stuff are correct (maybe this is a wrong assumption!) 

I'm extremely unfamiliar with this networking stuff (as is probably painfully obvious) but I would very much appreciate any help.


Thanks!

---

