---
title: "Network Manager auto starts all interfaces"
date: 2010-12-10
forum: Networking &amp; Wireless
---

### Post by emunson on 2010-12-10
I have been using WICD because of this problem but my company has started using a Cisco VPN and I'd like to integrate the VPN front end with my network management tool.  My problem is that NetworkManager always brings up the wireless interface on my laptop, even when wired is available.  There is no obvious method to configure this behaviour without manually disabling wireless when I plug in.  Is this possible currently?

---

### Post by iponeverything on 2010-12-10
I right click on nm go and to "edit connections" -> "wireless" I then choose the wireless network and un-check the "connect automatically" box. 

I do think it would be nice if there was more fine grained control nm behavior, but it's not that big a deal to me..

---

### Post by emunson on 2010-12-16
It is really unfortunate if that is the best control option we have.  nm should be able to handle only starting a preferred interface when available and falling back otherwise.

---

### Post by grahammechanical on 2010-12-16
May I quote from the network manager documentation?
> 
Network Manager aims for Network Connectivity which "Just Works". The  computer should use the wired network connection when it's plugged in,  but automatically switch to a wireless connection when the user unplugs  it and walks away from the desk. Likewise, when the user plugs the  computer back in, the computer should switch back to the wired  connection. The user should, most times, not even notice that their  connection has been managed for them; they should simply see  uninterrupted network connectivity.

Regards.

---

### Post by emunson on 2010-12-17
If it actually did that, that would be great.  WICD would not bring the wireless up until necessary.  Also, when I remove the wire and the wireless was brought up I have to disconnect and reconnect to get the routes right.  It isn't a feature to bring up both interfaces, it is a bug.

---

