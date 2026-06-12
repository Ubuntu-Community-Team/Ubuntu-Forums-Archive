---
title: "ubuntu cant connect to a win7 share on another router?"
date: 2012-12-01
forum: Networking &amp; Wireless
---

### Post by sdowney717 on 2012-12-01
I can connect the win7 pc to my ubuntu pc using 
run then \\192.168.1.103 and can map network folders.
I can view my ubuntu shares and use them in win7 explorer.
I can ping the ubuntu machine from win7

I can not connect my ubuntu pc to the win7 shares
I can not ping the win7 machine from ubuntu

I can use the Chrome remote desktop plugin to control the win7 PC inside the chrome browser. Works using the internet I think not the LAN

win7 pc is at 10.0.0.2
ubuntu pc is at 192.168.1.103

since win7 can see the ubuntu shares, It should be possible to work other way too?
I dealt with another router and sharing by forcing it to not use DHCP.
This router though I would like to keep it as it is set.
ping pics etc...

---

### Post by 2F4U on 2012-12-01
Is there a firewall either on the Windows machine or on one of the routers?

---

### Post by sdowney717 on 2012-12-01
> **2F4U said:**
> Is there a firewall either on the Windows machine or on one of the routers?

I dont really know, how to tell?

---

### Post by sdowney717 on 2012-12-01
tried various settings on-off no diff on the ping

---

### Post by sdowney717 on 2012-12-01
must be a feature!
to be able to ping and share up the chain
but not be able to go the other way.

I suppose the only solution is to turn off DHCP on the netgear router.
Last time I did that, I could no longer get into the settings and had to do a factory reset on it.

What will happen to the wireless part of a router where DHCP is off?
Which router manages to wireless password?

---

### Post by sdowney717 on 2012-12-01
I just thought of an idea. 
Simply install ubuntu one on the win7 pc and sync the folders.
This way the lan networking is not an issue.

I was also wondering about static routes that could be set up in the 192.168.1.1 router? Could that somehow show a path back to the 10.0.0.1 router?

---

### Post by sdowney717 on 2012-12-01
yes, static routing is supposed to work as it says here.

[http://homekb.cisco.com/Cisco2/ukp.aspx?pid=80&login=1&app=search&vw=1&articleid=17589](http://homekb.cisco.com/Cisco2/ukp.aspx?pid=80&login=1&app=search&vw=1&articleid=17589)

My old GateWay router has the exact setting pages as listed with the Cisco router used in the example

When I tried setting a static route, it kept bumping the IP assignment of the netgear router that connects the win7 PC.
So it never worked.

I was setting destinaton ip to 10.0.0.2 (assigned ip for win7 pc from netgear router
mask 255.255.255.255
gateway 192.168.1.105 (assigned ip from gateway router to the netgear router)

every time I did that, the gateway router bumped the ip assignment of the netgear router from 192.168.1.100 or 192.168.1.105

???
so what did I do wrong?

---

