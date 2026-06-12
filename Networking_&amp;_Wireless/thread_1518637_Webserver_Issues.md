---
title: "Webserver Issues"
date: 2010-06-26
forum: Networking &amp; Wireless
---

### Post by pepsifx357 on 2010-06-26
Hey guys, I install apache2 and got it working, when I lookup "localhost" in my firefox.  But I can't seem to connect using the internet IP address.

So here is my setup.

Macbook Pro DHCP ->Router DHCP(Port 80 and 21 Forwarded to my IP)->Bellsouth Modem(Also port forwarded 80 and 21 to my router)

I'm also using DynDNS.com to update my IP address with my domain name.  I have this service turned on my router and it says it's working.  I haven't set this up in a while so I'm trying to figure out what I'm missing.


Linux ben-laptop 2.6.32-22-generic #36-Ubuntu SMP Thu Jun 3 22:02:19 UTC 2010 i686 GNU/Linux

Many thanks

Ben

---

### Post by pepsifx357 on 2010-06-27
Day 2, same thing.  I've done this quite a few times now and this time I can't seem to get it working.  Any help?

Edit:  Just got through setting up the FTP server and I still can't connect over the internet.

Edit 2:  I tried to do a port scan on my internet IP and it says my IP cannot be found.  What's the deal?

Thanks

Ben

---

### Post by keithweddell on 2010-06-27
Are you doing this from inside your network - that is behind the router?  If so, your external IP address won't work.  You will need to use the local IP address which is usually in the rand 192.168.?.? or 10.?.?.? Or else you should try from a computer outside of your network.

Keith

---

### Post by pepsifx357 on 2010-06-27
I've kinda got it to work.  I had to reset the modem and setup the port forwarding again.  When I type the internet IP I can get to my web page, but I still can't get dyndns.com to forward the domain name to the IP address.

For the purposes of this thread, the problem was solved by resetting the modem and setting it up again.  I have another thread for the dyndns forwarding.

---

