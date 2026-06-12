---
title: "IP Address of CAM changes"
date: 2013-01-31
forum: Networking &amp; Wireless
---

### Post by fdrake on 2013-01-31
Hi there.
  In my store we have 2 IP cameras connected to my router (Cisco-Linksys E1200) which is connected itself to the brodband modem (MOTOROLA ; isp comcast).
I do have with comcats my static ip so that I can see from outside (home/office) with the browser the streaming of the cameras on different ports. I do have a problem sometimes. Because the port are forwared sepecifically to the ip of the cameras if the router reboots or looses power I have to reconfigure again the port forwarding feauture with new ip since the cameras have a different ip. 

Question: Is there any way I can stick an Ip to a specific device (MAC address) with my router?

---

### Post by ahallubuntu on 2013-01-31
You can reserve a specific IP for any device attached to your router.  Most routers have this feature - it's probably called "DHCP reservation."  Basically, it sees the MAC address (hardware address) of the attached device and assigns it the requested IP.  Poke around your router config (probably go to [http://192.168.1.1](http://192.168.1.1) ) and see how to do it, varies by make/model of router.

---

### Post by papibe on 2013-01-31
Hi fdrake.

You need to create a DHCP reservation with a LAP IP that is outside your DHCP range.

Take a look at this [example]("http://seoroot.com/blog/linksys-routers/linksys-e1000-wireless-router-dhcp-reservation.html").

Hope it helps. Let us know how it goes.
Regards.

---

### Post by fdrake on 2013-01-31
@papibe, @ahallubuntu

thanks a lot guys. I got it working. I thought it 'd harder to solve :D

@ahallubuntu thanks for the link!

---

