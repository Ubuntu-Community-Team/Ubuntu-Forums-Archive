---
title: "Internet will only get to Google"
date: 2010-01-23
forum: Networking &amp; Wireless
---

### Post by G Force on 2010-01-23
Just installed Ubuntu for the first time and got the network up but only seem to be able to get to the google website via Firefox which seems bizarre.  Every other URL just hangs.  

Tried also putting the router IP address in which prompted me for user ID and password but no web page came back. I'm fairly new to the Linux thing and so far have just followed the plain install with no additional installations.  

Any ideas anyone.

Thamks,

G.

---

### Post by x33a on 2010-01-23
try pinging the websites you want to connect to.

example
```
ping google.com
```also, try changing the dns servers.

---

### Post by HeadHunter00 on 2010-01-23
Noo, it means that you are not connected to internet. Ubuntu version firefox's default homepage, which is chrome://ubufox/content/startpage.html doesn't require you to be connected to internet. I had the same problem

---

### Post by G Force on 2010-01-23
I'm definately on the internet.  I can ping the websites OK e.g. [www.ubuntu.com](www.ubuntu.com) comes back in 20ms but the page doesn't come back in Firefox.  I've tried a few more pages and some come back but most don't.

DNS servers are currently picked up from the router and work fine for all other (Windows) PCs in the house (including the other W7 boot partition of this PC).  Any reason why they wouldn't work for Ubuntu?  Which alternatives would you recommend?  Should they be changed on the router or the Ubuntu PC?

Thanks,

G.

---

### Post by asearle on 2010-01-23
I think I've got the same problem:  I can ping sites but they won't appear in Firefox.

I also find that when I try a software update most packages fail but a few get through.

I think that it is a problem with MTU and/or with IPv6 but I've tried changing the MTU and have disabled IPv6 (I think) but couldn't fix the problem.

This is an absolute pain because I can't do anthing until I get the nework up.

Any tips?  Anyone?

Regards,
Alan Searle

---

### Post by nitstorm on 2010-01-23
Have you tried disabling iPv6 in firefox???

1.in the address bar put type *about:config* and hit enter
2. say ok it might void the warranty and proceed
3. scroll down to see a line like this 
network.dns.disableIPv6 , click on it and change the boolean value to true. 

That might just make it work. If not i am sorry..

cheers!

---

### Post by asearle on 2010-01-23
I disabled it in Firefox and restarted firefox but still couldn't get any sites.

I tried pinging from a browser and that worked OK.

Arrgghh.  This is maddening.

But thanks for the tip.

Yours,
Alan

---

### Post by Iowan on 2010-01-23
[Here]("http://ubuntuforums.org/showthread.php?t=1376506") is a thread that goes through some MTU checks.

---

### Post by G Force on 2010-01-23
Yes Iowan, that thread helped.  Typed in "sudo ifconfig eth0 mtu 1492" and it all sprang into life.  So its the MTU - whatever that does.

have now set that in the network settings box which will hopefully make it permanent - will let you know.

Cheers,

G.

---

### Post by G Force on 2010-01-23
Well 4 hours and a few reboots later and everything is working.  Just got the wireless working too.   So I'd say problem is solved.

Thanks again,

G.

---

### Post by asearle on 2010-01-24
For me too the command ...

sudo ifconfig eth0 mtu 1492

... got it working.

But I need to run this every time I boot so I'd be interested to hear of a permanent fix.

The strange thing is that in my (graphical) Network settings MTU is set to 576.

I'm confused but it's working so I am pleased.

Thanks for the tips.

Cheers,
Alan

---

### Post by G Force on 2010-01-24
Alan,

I changed the setting in the Network Connections GUI.  Edited the Eth0 connection and set the MTU to 1492 under the "wired" tab.  That held it permanently.

G.

---

