---
title: "Current Connection Not Shown in Network Manager"
date: 2009-11-07
forum: Networking &amp; Wireless
---

### Post by unperson on 2009-11-07
I just upgraded to Karmic.  Before that I ran Jaunty and before that Intrepid... My machine is currently connected by a wired connection (static IP) that I setup using the GUI in some earlier version of Ubuntu and it is working just fine; however, the Network Manager Applet shows me as not connected and doesn't seem to register the existence of this connection in any way.  How can I get the Network Manager Applet to see and manage my wired connection?

This is not currently a problem, but at some point I might want to change the properties of my connection, and Í'd like to be able to do that through the GUI.  I'd also like to be able to use Network Manager for other tasks, like setting up a VPN, but I think that first it would need to recognize my connection. 

I think this problem has existed since maybe Jaunty.  IIRC they significantly changed the GUI used for managing network connections, and I'm guessing that something on the back end was changed, which would be why the new GUI doesn't know a connection already exists.  Unfortunately, I'm not familiar enough with the nuts and bolts to figure out any more than that.  I can say that ifconfig shows eth0 with the IP address as you would expect.

---

### Post by unperson on 2009-11-07
I'm not sure of the original source of the problem, but it seems that my wired network connection was configured in /etc/network/interfaces.  I was told that Network Manager will not interact with that configuration.  

I used the command 'ifdown eth0' to bring down the interface, then I commented out all the lines in /etc/network/interfaces that referred to eth0. I then proceeded to select "Edit connections" in the Network Manager Applet and add a new interface under the Wired section.  This didn't appear properly in the list until I reset the machine, but after doing that I was able to start the network through Network Manager with no problem.

---

