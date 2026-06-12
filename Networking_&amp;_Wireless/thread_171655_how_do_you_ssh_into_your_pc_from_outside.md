---
title: "how do you ssh into your pc from outside?"
date: 2006-05-07
forum: Networking &amp; Wireless
---

### Post by zasf on 2006-05-07
Hi, I'd like to ssh into my pc at home wich is behind a router. I installed sshd and made sure that I can ssh into the box from another pc in my LAN, using
```
ssh user@192.168.1.99
```

where 192.168.1.99 is the local static ip assigned by me to the box I want to ssh to.

What I miss it how to ssh into the same box from work using putty. I forwarded port 22 from router's setup to 192.168.1.99. Before trying to do it from work, I'm trying from the second pc to

```
ssh user@aa.bb.cc.dd
```

where aa.bb.cc.dd is my dynamic ip (assigned by ISP). But it doesn't work, saying "connection refused".

I strongly believe I won't be able to do it from work either with current setup. Am I missing something? Isn't port forwarding enough?

EDIT: If I do

```
sudo nmap -sS 192.168.1.99
```

I see port 22 right open, but the same doesn't occur with the router. Even if I forwarded some other ports with success (ie emule, warcraft and others).

---

### Post by gibson on 2006-05-07
```
ssh user@aa.bb.cc.dd
```

this will not work if the box you are ssh from is on the same internal network, it will only work internally with your network ip (not the ISP one).

Get it set up with forwarding, then try it from a connection outside your network e.g. a friends house

Im no network guru, but im sure that is your problem as i think ive had it before but that was a long time ago :) .

all the best

---

### Post by zasf on 2006-05-12
[QUOTE=gibson]```
ssh user@aa.bb.cc.dd
```

this will not work if the box you are ssh from is on the same internal network, it will only work internally with your network ip (not the ISP one).

Get it set up with forwarding, then try it from a connection outside your network e.g. a friends house

Im no network guru, but im sure that is your problem as i think ive had it before but that was a long time ago :) .

all the best[/QUOTE]

from outside my local network, it works. Still I don't understand why it doesn't work from the local network. If I ping my ASP IP from local network it works. Thank you anyway.

---

### Post by moterpent on 2006-05-12
> Before trying to do it from work, I'm trying from the second pc to...

Zasf, where is "the second pc"?  Is this inside (192.168.1.x) or outside the router?

---

### Post by zasf on 2006-05-12
[QUOTE=moterpent]Zasf, where is "the second pc"?  Is this inside (192.168.1.x) or outside the router?[/QUOTE]

The second pc is inside the local area network, from that pc I ping ping the ssh server or ssh into it using the local address 192.168.1.x.

From the second pc I can ping the ssh server using ISP IP but not ssh into it (it only works with 192.168.1.x IP, why?).

From another pc, outside the LAN, I can ssh into she ssh server using putty.

---

### Post by Iowan on 2006-05-12
What do you mean by > ping the ssh server using ISP IP Guessing again (sorry LH317), but it sounds like your firewall may be blocking what appears to be a spoofed internal address appearing on an external port (or vice-versa)

---

### Post by moterpent on 2006-05-13
> The second pc is inside the local area network, from that pc I ping ping the ssh server or ssh into it using the local address 192.168.1.x.
OK.  I understand what's going on now.  Here's the deal.

Whenever you try to do anything to the public IP from a private address you are talking to the router and not your machine.  The router does not route and forward your packets back into the private network.  It has no reason to think that it should because the request is coming from the private side of the network.  After all, for most cases, the router is thinking why would you want to route a packet that originates from the same physical network?  That would be like walking to your next door neighbor's house by way of the local supermarket.

> From the second pc I can ping the ssh server using ISP IP but not ssh into it (it only works with 192.168.1.x IP, why?).
Actually you aren't pinging the ssh server.  You are pinging the router.  This is also why when you run "nmap" from an internal IP to your ssh server you can't see port 22 open.  It's because it's port scanning the router and not your ssh server.

> From another pc, outside the LAN, I can ssh into she ssh server using putty.
Yes, this is the scenario that the router is set up to deal with.  Port forwarding is only taking place from requests made on the public side of the network.

Hopefully this makes sense.  If not, let me know and I'll do my best to try to explain it better.  

What are your reasons for wanting to be able to connect to your servers various services from internally using the public IP?  Testing?  Common DNS resolution?

---

### Post by zasf on 2006-05-13
[QUOTE=moterpent]OK.  I understand what's going on now.  Here's the deal.

Whenever you try to do anything to the public IP from a private address you are talking to the router and not your machine.  The router does not route and forward your packets back into the private network.  It has no reason to think that it should because the request is coming from the private side of the network.  After all, for most cases, the router is thinking why would you want to route a packet that originates from the same physical network?  That would be like walking to your next door neighbor's house by way of the local supermarket.[/QUOTE]

This makes sense

> Actually you aren't pinging the ssh server.  You are pinging the router.  

Ok, so the router answers back when pinged.

> This is also why when you run "nmap" from an internal IP to your ssh server you can't see port 22 open.  It's because it's port scanning the router and not your ssh server.

Ok, if port 22 is forwarded, isn't it open on the router as well as the ssh server?

> Yes, this is the scenario that the router is set up to deal with.  Port forwarding is only taking place from requests made on the public side of the network.

Hopefully this makes sense.  If not, let me know and I'll do my best to try to explain it better.  

What are your reasons for wanting to be able to connect to your servers various services from internally using the public IP?  Testing?  Common DNS resolution?

Testing, I wanted to make sure everything was setted right before trying to ssh into the box from a remote location.

Thanks for the help but now I have another question :mrgreen: 
The router has a http configuration, so that if you enter the router's IP (public or private from local network) in firefox bar you can set forwarding and other tweaks. I can't access the web configurator, using public ip from outside local network, is that standard? Is it a protection thing that doesn't enable other people to access your router? What happens with your router? It could be very nice to forward some ports remotely/open then just when you need it. Thanks again for supporting.

---

### Post by moterpent on 2006-05-14
> The router has a http configuration, so that if you enter the router's IP (public or private from local network) in firefox bar you can set forwarding and other tweaks. I can't access the web configurator, using public ip from outside local network, is that standard?
A lot of routers have a setting for this.  You'll have to look through the web interface menus or with the documentation that came with your router.  For example with many Linksys routers, from the web interface, click on the "Administration" link/tab at the top and click the "Enable Remote Management" option.  You can also choose to encrypt the sessions using SSL, select a port other than 80 for the interface to run on etc.

How this works and whether or not it is an available option will vary from maker to maker and from model to model.

> Thanks again for supporting.
My pleasure.  I'm glad to help.  Let me know how it turns out.  :)

---

