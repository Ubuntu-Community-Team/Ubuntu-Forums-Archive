---
title: "Network Manager Applet shows no Connection, even though I can ping"
date: 2009-06-17
forum: Networking &amp; Wireless
---

### Post by Augsburg on 2009-06-17
Hello all.

I am having a very frustrating problem, and I'm hoping someone can help.

I am setting up a wireless mesh network.  I am trying to connect my client computer to an Asus WL-330g (Access Point Mode).  The network is called asus_2.  It's IP address is set to 192.168.2.1. The computer it is connected to has IP address 192.168.2.2 (connect by ethernet to the AP).  It's wireless card is connected to a separate network.

My problem is that my client computer (running Jaunty) seems to be unable to recognize a connection to asus_2.

Here's what I did:
Using the Network Manager Applet on the upper toolbar, I selected asus_2 from the menu.  As the icon switched to display a 'trying to connect' graphic, I set my IP address to 192.168.2.3, and added a default gw route at 192.168.2.2.  Once done, I was able to ping to 192.168.2.1 (the Access Point).  So, at this point, I knew I had a solid connection.  But after a few seconds, the Network Manager Applet still hasn't shown a network connection, and it cuts off and connects to a different network.
What can I do to either allow it to connect to this network or disable it from disconnecting?

I've tried iwconfig from the command line (and pump to refresh the connection), and iwlist finds asus_2 just fine.

Thanks in advance for your help!

-Phil

---

### Post by Brandon Williams on 2009-06-17
By 'mesh network', I think you mean an 'ad-hoc' network, right?

Also, when you say 
> As the icon switched to display a 'trying to connect' graphic, I set my IP address to 192.168.2.3, and added a default gw route at 192.168.2.2.
Are you adding the address manually from the command line? If so, that explains the problem, I think. 

Network-manager wants to either manger everything about the network connection, or manage nothing about it. If you want it to handle this ad-hoc network for you, then right click on the icon, select 'Edit connections...', click on the 'Wireless' tab, and Add a new network. If you check the 'Connect automatically' box for the new network, it will automatically use those settings when any other computer in your mesh network is advertising.

I haven't tried this with an ad-hoc network, since I don't use them, but there certainly appears to be support for this in the interface.

---

### Post by Augsburg on 2009-06-17
Thanks for your help!

Although that wasn't exactly what I needed, knowing that Network Manager likes to do everything on its own was enough.  I editing the connection I had and changed the settings from DHCP to manual, added in the ip address and gateway, and the route I needed.  I also checked the box on both that network and the one I'm currently on to allow all users to connect (for some reason that helped).

It connects now and works great!

---

