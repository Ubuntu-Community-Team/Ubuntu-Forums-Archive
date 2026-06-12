---
title: "Ubuntu server causing browsing issues for other devices."
date: 2012-08-05
forum: Networking &amp; Wireless
---

### Post by Kurir on 2012-08-05
Hello everyone,

I'm new to ubuntu but have a major work to do for uni that involves a server. The server is sitting behind a router with a static ip, both for the router and the server itself. Port forwarding has been set up for ports 22 and 21 so that I can work on the server from home.

However, there are other devices also using the network that the server is on. A macbook and an iMac. The client for the project wants to use the server as a webserver for their own website but forwarding port 80 to the server interrupts the browsing on other machines, as the reply message to a http request comes in on port 80.

Any ideas of how I can get around this so that they can have a web server and browse the web on other machines at the same time?

External hosting is not possible and neither is changing ports used on other devices.

Thanks,

Kurir

---

### Post by Doug S on 2012-08-06
Hello and welcome to Ubuntu forums.
Your description of what you want to do is fairly normal, and many do it.
This part:> ... but forwarding port 80 to the server interrupts the browsing on other machines, as the reply message to a http request comes in on port 80.
I don't think is correct, or I don't understand. The reply to an out going http request, say from the macbook or imac, woud come back on same port as the outgoing request, not port 80. So there should not be an interruption problem. If there is, we will need some more information.

---

### Post by Kurir on 2012-08-06
> **Doug S said:**
> Hello and welcome to Ubuntu forums.
Your description of what you want to do is fairly normal, and many do it.
This part:I don't think is correct, or I don't understand. The reply to an out going http request, say from the macbook or imac, woud come back on same port as the outgoing request, not port 80. So there should not be an interruption problem. If there is, we will need some more information.

Well I know when I had my client, who is a fair way away, set up port 80 and then try to browse, she couldnt get anything in her browser anymore, and when she removed it, she could. 

So its going out on port 80 on the macbook and coming back into the router on port 80, which then gets routed to the server instead of the macbook. 

This is the problem, as I cant change the outgoing ports on the macbooks etc as I dont have general access to them.

Thanks for the reply though.

Kurir

Edit: After rereading your post, I see your confusion. The problem wasnt browsing to the web server, but to external pages, such as google or facebook, from the macbook or other devices on the network.

---

### Post by Doug S on 2012-08-06
We will need more detail about the changes made to do the port forwarding on the router.
It should be possible to do what you want, but perhaps not with whatever router you are using.
If the macbook is doing normal browsing to external sites, the requests source port would not be port 80, only the destination port. If port forwarding is done only on incoming port 80 requests from the external interface on the router, then things should work as you want.

---

### Post by Kurir on 2012-08-06
Hi,

The router being used is a netcomm nb6plus4w. The port forwarding is done through the routers own port forwarding interface in the routers browser page.

Achieved by giving the server a static ip behind the router(which has its own external static ip) and then forwarding port 22, 21 etc to the server instead of to the normal destinations.

I really dont have too much experience with networking, it bores me most of the time, but I have the most experience in my group so I am doing it.

If you need any more information, please let me know.

James

---

### Post by Doug S on 2012-08-06
I looked at the manual for the nb6plus4w, and it should be able to do what you want.
So now we have to figure out why it doesn't seem to be doing the correct things.
 
I have seen others on this forum recommend this site: [http://portforward.com/](http://portforward.com/)
and for HTTP for that router: [http://portforward.com/english/routers/port_forwarding/Netcomm/NB6PLUS4W/HTTP.htm](http://portforward.com/english/routers/port_forwarding/Netcomm/NB6PLUS4W/HTTP.htm)
and for HTTPS: [http://portforward.com/english/routers/port_forwarding/Netcomm/NB6PLUS4W/HTTPS.htm](http://portforward.com/english/routers/port_forwarding/Netcomm/NB6PLUS4W/HTTPS.htm)
 
Is that what you are doing?

---

### Post by Kurir on 2012-08-06
We hadnt tried to forward https, only http. It is a little different to that with firmware changes etc but generally the same. We had it forwarded for both tcp and udp, port 80 to port 80, specifying the internal ip address as well.

So yes, what I hope was done is that, as that is pretty much what we did to forward ports 22 and 21, and I did try to walk the client through forwarding port 80, as she has some technical knowledge at least, better then most people I've tried to teach before.

I am going to try remote desktoping to her mac later today or tomorrow and do the port forwarding myself, but any ideas is much appreciated :)

Kurir

---

### Post by Kurir on 2012-08-07
Bump because im a bit desperate.

---

### Post by Kurir on 2012-08-08
No more ideas?

---

### Post by Kurir on 2012-08-10
So, I've used RDP to get into the system and access the router from there, and forwarded port 80 to the server, but couldnt then access the apache server from externally. It apparently does work internally when I dont have it forwarded, but I cant access it externally when i forward port 80

Apache must be using port 80 for connections on the same network to be able to reach it, but for some reason port forwarding doesnt let me access it from externally.

Any ideas?

---

### Post by Kurir on 2012-08-13
Ok I think I figured it out, though I havnt yet tested the local network since I got access externally. The only problem I ended up finding was that my site was looking in the wrong document root and after fixing that and reenabling the sites it now works.

Thanks for trying to help.

---

