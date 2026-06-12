---
title: "Help with D-Link IP Camera"
date: 2012-10-16
forum: Networking &amp; Wireless
---

### Post by Derek Karpinski on 2012-10-16
I have a dlink DCS-930L.  I also have two routers, both with dd-wrt.  One router is N-band only, the other is G band only.

Everything works fine as long as I'm viewing the webcam ([http://10.50.1.107:8080](http://10.50.1.107:8080)), from the computer that is physically hooked up to the router.

I cannot view the webpage from any other device on my LAN.

My set up looks like this:
------ = cat 5
**** = wireless

PC<---->N-band router(dhcp server)<------>G-band router(AP)<*******>IP Camera

I tried from my wife's laptop, which connects to the N-band router wirelessly, and the webpage won't load.

I tried from my phone, which is connects to the G-band router wirelessly, and the page won't load.

I get no response from ping from any device except for the PC that is physically hooked to the router.

I'm sure it is something very simple like ports need to be opened or forwarded, but I'm at a loss.

EDIT:
It does not matter which router I connect to over wireless, I cannot see it other than from the PC connected to the router.

Furthermore, if I connect the camera directly to the router with a LAN cable, I can see it from anywhere.

---

### Post by jingaling on 2012-10-18
Since it won't connect via multiple machines, phone and multiple places (and multiple OS's) then it clearly isn't an Ubuntu issue. I'd head over to the support forums of the camera manufacturers.

Something to try though (just so you get something back):

Can you ping the camera from the wireless devices?

Does the wireless network(s) have the same subnet as the physically connected LAN? It may sound like a strange question but it's common for Wireless AP's to have a different subnet from the rest of the LAN.

Can the wireless devices ping the machine that does connect to the camera?

Is port 8080 allowed to pass through the AP's firewall?

Hopefully having the answers to some of the questions will point you in the right direction of where the problem is.

Good luck!

---

### Post by Derek Karpinski on 2012-10-20
> **jingaling said:**
> Since it won't connect via multiple machines, phone and multiple places (and multiple OS's) then it clearly isn't an Ubuntu issue. I'd head over to the support forums of the camera manufacturers.

Something to try though (just so you get something back):

I will ask there, but I like the people on this forum, and they seem to be the smartest bunch.  I'm not sure this problem is specific to this model camera.

> **jingaling said:**
> Can you ping the camera from the wireless devices?

No.  It won't even show up on a network inspector (Fing) on my android phone.

> **jingaling said:**
> Does the wireless network(s) have the same subnet as the physically connected LAN? It may sound like a strange question but it's common for Wireless AP's to have a different subnet from the rest of the LAN.

Everything is on the same subnet.  I have about 7 wireless devices in my network.  3 of them running through the G-band router, the rest through the N-band.  I can see all of them, and they all talk together nicely.  All are on 10.50.1.* subnet.

> **jingaling said:**
> Can the wireless devices ping the machine that does connect to the camera?

Yes.  Let's call this my 'server' since it runs Samba, squeezebox server, ssh, apache, etc.  All devices are using this computer's services in some way.

> **jingaling said:**
> Is port 8080 allowed to pass through the AP's firewall?

Yes, on both routers.  Also, ports 554, and 5556-5559 per the manual.

> **jingaling said:**
> Hopefully having the answers to some of the questions will point you in the right direction of where the problem is.

Good luck!

Thank you!

---

### Post by pmsoares on 2012-11-21
Hi.

I had the same problem in the last days after messing with the router configurations.

After some digging and time to trace the problem, I found the cause for not being able to connect from any wireless devices (laptop, tablet, android phone, etc...) to the D-Link camera.

You have to disable **AP Isolation** mode on the AP and/or Router.
The AP Isolation isolate all connected wireless stations so that wireless stations cannot access each other through WLAN.

Hope it helps solve your problem.


Bye,
Pedro Soares

---

### Post by dmac1blah on 2012-11-23
I have to thank you for this post I had an issue with security cameras in the same way and I had overlooked the AP Isolation, disabled it and it worked.  :P
 
 
> **pmsoares said:**
> Hi.
 
I had the same problem in the last days after messing with the router configurations.
 
After some digging and time to trace the problem, I found the cause for not being able to connect from any wireless devices (laptop, tablet, android phone, etc...) to the D-Link camera.
 
You have to disable **AP Isolation** mode on the AP and/or Router.
The AP Isolation isolate all connected wireless stations so that wireless stations cannot access each other through WLAN.
 
Hope it helps solve your problem.
 
 
Bye,
Pedro Soares

---

### Post by Derek Karpinski on 2013-01-11
> **pmsoares said:**
> Hi.

I had the same problem in the last days after messing with the router configurations.

After some digging and time to trace the problem, I found the cause for not being able to connect from any wireless devices (laptop, tablet, android phone, etc...) to the D-Link camera.

You have to disable **AP Isolation** mode on the AP and/or Router.
The AP Isolation isolate all connected wireless stations so that wireless stations cannot access each other through WLAN.

Hope it helps solve your problem.


Bye,
Pedro Soares

Yep.........that did it..........thanks!

---

