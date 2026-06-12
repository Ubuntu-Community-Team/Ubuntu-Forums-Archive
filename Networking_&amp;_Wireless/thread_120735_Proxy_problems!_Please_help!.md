---
title: "Proxy problems! Please help!"
date: 2006-01-23
forum: Networking &amp; Wireless
---

### Post by jestersmurf on 2006-01-23
Hey.

Ive been using Ubuntu for about a year now, and I love it! That said i never really got my laptop up and running like I want it to with Ubuntu. So for a while now its been a Windows machine, but now im gonna give it a try again!

Currently im trying with the new Dapper Flight 3 install, and so far no hardware problems what so ever! SUCCES! But I am however behind a proxy server becuase im at a school right now!

**The problem is that I cant get Dapper to get through the proxy once its installed, the wierd thing is that during the install it connects fine to the web, but once its up and running i cant connect!**

With the Windows running I have no problems but I just cant seem to get it working with Dapper, might just be I dont know exactly how to set it up!

**Is there a way to config and test the proxy settings using the prompt?**

Please help me with this, I really want my machines Microsoft free!!!

Jestersmurf

---

### Post by jestersmurf on 2006-01-24
Well then... I solved some of the problem!

I found out that the DNS server in this network for some reason didnt giv off alle the info it should, so i typed the IP instead of the DNS name in Firefox, and SUCCES! now I can acces the web with Firefox!

But im still having problems with APT and therefor Synaptic! I think the main problem might be that there is an "@" in my password, so non of the other solutions in this forum works!
[B]
Please help, i feel like im only using half of what ubuntu is capable off!

To sum up the problem:
APT cant acces through the proxy!
Dosnt work to set up the proxy i the Gnome GUI![/B]

---

### Post by spd106 on 2006-01-24
Have you tried changing the proxy settings in synaptic -> preferences -> networks?
What's in the /etc/hosts file?

If you can ping a remote server then it must be a setting somwhere in the program concerned.

---

### Post by jestersmurf on 2006-01-24
Ive tried configuring synaptic, but there is no prompt for user og pass.

Here's my /ect/hosts:
----------------------------------------------------------
127.0.0.1 localhost michael-laptop
127.0.1.1 michael-laptop

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
10.112.127.203 hsgs22
------------------------------------------------------

"hsgs22" is the proxy-server, and the port is 8080.

Im really stuck here, and I think it might be because of the "@" in my password!
Ive read the syntax witch is used is somthing like "http://username:password@proxy:port" so it seems like APT and synaptic cant get past the "@"....

---

### Post by jestersmurf on 2006-01-24
Ive tried configuring synaptic, but there is no prompt for user og pass.

Here's my /ect/hosts:
----------------------------------------------------------
127.0.0.1 localhost michael-laptop
127.0.1.1 michael-laptop

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
10.112.127.203 hsgs22
------------------------------------------------------

"hsgs22" is the proxy-server, and the port is 8080.

Im really stuck here, and I think it might be because of the "@" in my password!
Ive read the syntax witch is used is somthing like "http://username:password@proxy:port" so it seems like APT and synaptic cant get past the "@"....

---

