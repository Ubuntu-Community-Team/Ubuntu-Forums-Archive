---
title: "Not detecting IP/DNS setting on Netgear router"
date: 2009-06-24
forum: Networking &amp; Wireless
---

### Post by thicklizzie on 2009-06-24
I am a new Ubuntu user -ABSOLUTE BEGINNER! I have been trying to set up a Netgear WGR614v9 router on Dell mini. I have another computer (with no wireless card) connected to the router and it gets to the internet just fine. I have gone through the initial process of contacting the Netgear IP and ping it with the mini, but the system does not pick up my DNS, subnet mask, gateway etc setting when I test/apply as directed. I have been trying for a week now to get it to work.
 
I don't know what or where to find my IP, subnet, gateway or how to set up the WPA(?) security manually.
 
HELP! I thought Ubuntu would be simpler bare bones than Windows but it waaaayyy more complicated to get even the littlest thing even started and working. 
 
Please help or I am sending the computer back to Dell!!!
 
Thanks

---

### Post by decoherence on 2009-06-24
Hi there,

Did your Dell come with Ubuntu pre-installed?

First thing to do is hook your Mini up with a wire and confirm that it can get online that way.

By default your router should use DHCP which will automatically assign your IP, subnet and gateway.

If you click the NetworkManager icon, do you get a list of wireless networks? (the network manager icon is in the top toolbar, on the right side... looks like the Windows LAN icon.... at least on my system.

If you go to Applications > Accessories > Terminal and type the following
```

sudo lshw -C network
```
What output does it give you? (just copy/paste it) (note, it will ask for your password. When you type it, nothing will appear on the screen. Just type and hit enter. This is normal)

This is all supposed to be handled automatically. Generally the only time it isn't is when Ubuntu doesn't have a driver for the wireless card. That's why I ask if the Dell came with Ubuntu pre-installed.

---

### Post by thicklizzie on 2009-06-24
Hi,
 
Thanks for answering so quickly. 
 
Yes Ubuntu came pre-installed from Dell...Hardy Heron.
 
The wireless has always worked okay.  It has been set up to work and I have connected consistently to the internet at Starbucks, at my brother's home with his network, etc.  I have even been able to connect to the internet with someone else's  unsecured wireless network (though they cut me off after a day).  I just can't seem to get my own network to get up and running.  I did not set up my wired computer through the router, I just plugged it in and it worked.  Is this something I have to do?

---

### Post by jonobr on 2009-06-24
Hey thicklizzie

Welcome to the forum

I think you need to be a bit easier on yourself.

Imagine you never used mac before and somebody handed you a computer..
Its going to take some time. And people in the forums are always helping 

It sounds as if your router is doing something more here.,

If you connecting to the wireless, I would recommend as quick test, just disable security on the ap for a second to see if it connects ok.

Reconnect to the network using a sudo dhclient command from the terminal window

When that works, check the result of ifconfig to see if your assigned an ip address..
Dont forget to resecure your network.



One other reason why it may not be working is if your ap is doing a check of mac address before assigning IPs or if your router is not using DHCP and you should be using a static connection

---

