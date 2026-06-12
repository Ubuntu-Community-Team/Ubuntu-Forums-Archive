---
title: "VPN when connecting to Internet with Browser"
date: 2009-07-11
forum: Networking &amp; Wireless
---

### Post by ukeitaro on 2009-07-11
Hi Everyone,

The place where I'm currently staying for the next few months provides Internet access.  However, gaining access requires going to a login page through a web browser and entering my user account and password.  I then have to leave this login page open in my browser in order to maintain my Internet access.

This procedure has worked well for general Internet use, but I've also been trying to connect to a VPN network.  Whenever I use vpnc, it says that I've successfully connected to my VPN network, but then a few seconds later my Internet connection breaks completely.  I'm guessing that my VPN connection, because it changes my IP address, is affecting my browser's ability to maintain my Internet access through the login page.

The weird thing is that I've been able to connect to my VPN network using Cisco VPN Client on Windows XP under VirtualBox, but my Internet connection won't break as before.  So what I've been doing is just leaving the login page open in Firefox on Ubuntu, but then I connect to VPN in Windows XP and then use the Internet from there.

The problem is that ideally I would like to connect to VPN under Ubuntu instead of Windows so that I can use all my Ubuntu applications and scripts.  Do you think there is a workaround to connecting to my VPN network on Ubuntu without breaking my Internet connection?

Thanks a lot! I appreciate the help!

---

### Post by The Cog on 2009-07-11
Lots of VPNs re-route your default route through the VPN. The Cisco VPN behaves like that. It may be that this is causing your browser to lose contact with the original internet access page. You can verify this by using the command **route print** before and after starting the VPN. 

If my guess is right, you will need to add a static route after starting the VPN, pointing to the access web page but NOT through the VPN. IF you can post the routing tables before and after the VPN, and can find the IP address of the access web page, we can figure out the command needed to do this.

---

