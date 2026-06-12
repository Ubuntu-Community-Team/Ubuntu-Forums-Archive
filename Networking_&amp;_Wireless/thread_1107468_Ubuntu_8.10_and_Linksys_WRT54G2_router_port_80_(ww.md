---
title: "Ubuntu 8.10 and Linksys WRT54G2 router port 80 (www) forwarding not working"
date: 2009-03-26
forum: Networking &amp; Wireless
---

### Post by ScottHuber on 2009-03-26
router port 80 forwarding not working, apache2 fails to respond Ubuntu 8.10 server and Linksys WRT54G2 

I have a Linksys WRT54G2 router hooked up to DSL.  I have port forwarding enabled on ports 20-21, 22, 80, 443, 8080.  My linksys has dynamic IP address around 71.131.xxx.xxx and internal to my network I have a static IP for my server at 192.168.1.51  My DHCP address range is above 192.168.1.100

I am using a dynamic DNS scheme through eNom which seems to work fine.

The http requests from the internet fail to connect to my internal Apache2 server.  It used to work 4 days ago.  I contacted my DNS service and they are not able to connect http to my server.  The ISP isn't either but it doesn't seem to be their problem.

I checked the Incoming and Outgoing logs on my router and it seems like the http request is bridging the router.  But I'm not 100% sure of this.  I am able to successfully http in on port 8080 to tomcat; meaning I get back the expected web page.  Internal to my network I am able to http to the server and get back the expected web page on 192.168.1.51.  I am able to ssh across the router as well.

I verified the syntax of my apache conf file is ok.  But when I do apache2 -X  I get back: bad user name ${APACHE_RUN_SERVER}  I tried putting my server in the DMZ but was still unable to get http response.

I had svn setup on my apache2 server but I commented out those lines in the configuration file just to be sure that wasn't the problem.  

I've restarted apache2 after every change and I've even rebooted the server.

I did an nslookup from my Windows XP laptop and the domain name resolves to the correct IP address.

Does anyone have any ideas or any suggestions that might help me?

Thanks for your time!

Scott Huber

---

### Post by superprash2003 on 2009-03-26
some ISP's block port 80.. try this online port scanner to see if port 80 is open [http://www.t1shopper.com/tools/port-scanner/](http://www.t1shopper.com/tools/port-scanner/) .. do you have firestarter or anything similar running..

---

### Post by ScottHuber on 2009-03-27
I did check with my ISP (at&t) and they weren't blocking port 80.

I just figured out part of the problem.  I used to have a server named ubuntu-server on internal IP 192.168.1.50 then I created a new server on IP 192.168.1.51 also named ubuntu-server. I then updated my router port forwarding from 192.168.1.50 to 192.168.1.51 and after a day or so powered off the old server x.x.1.50.  This seemed to work for a while.  But then I could no longer connect to the server from the internet.

I did an >sudo tcpdump -nni etho0 host 192.168.1.1
thanks to ( [http://digg.com/linux_unix/10_Best_Hacking_and_Security_Software_Tools_for_Linux?t=16609129](http://digg.com/linux_unix/10_Best_Hacking_and_Security_Software_Tools_for_Linux?t=16609129) )
and got some results showing that there was some arp for 192.168.1.50 still occuring.  So I set my new server to static IP 192.168.1.50 and boom everything works.  I can type in my domain name and pull up the correct webpage. 

Now I have to figure out what the deal was with the old ip address getting arp'ed.  And what I need to do so I can change the IP to 192.168.1.51, or whatever I wish.  Maybe there was something which remembered that ubuntu-server meant 192.168.1.50 even though that changed.  Any idea what that could be?

If I'm unable to figure it out without too much hassle, I'll be content to live with it at 192.168.1.50 for the time being and fix this issue at a later point.

Thanks!

Scott Huber

---

### Post by ScottHuber on 2009-03-27
My ubuntu-server has /etc/hosts with...

127.0.0.1       localhost
127.0.1.1       ubuntu-server.MyDomain       ubuntu-server

So I don't yet understand how this gets mapped to its real ip address.  

/etc/hostname has a value of...

ubuntu-server

/etc/network/interfaces has...

auto eth0
iface eth0 inet static
        address 192.168.1.50
        ...

---

