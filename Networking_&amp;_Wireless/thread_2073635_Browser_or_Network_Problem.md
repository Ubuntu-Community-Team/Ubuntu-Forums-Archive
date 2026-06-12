---
title: "Browser or Network Problem?"
date: 2012-10-20
forum: Networking &amp; Wireless
---

### Post by larrymeditates on 2012-10-20
Hi there, 

I've been using windows xp and a dsl router on my pc which has worked fine.   Then I installed ubuntu 12.04 LTS as a dual boot system and which comes with firefox.  When I clicked on the network connection it looked like it was connected but I kept getting a message on firefox that it can't connect to the server so I thought I should manually set the network settings.  I did that using the network info for the ppp adapter (ip address, default gateway, network mask, dns servers) for my IP, DSL Extreme, and an icon popped up saying I was connected but I still couldn't connect to the internet with firefox.  What's the problem?

---

### Post by uncaspi on 2012-10-20
You probably missing the route to the router.
Have a look at man route

---

### Post by efflandt on 2012-10-20
Most dsl modems for years are actually a modem/router that should handle  the PPPoE login and automatically give your computer a private LAN IP address.

What make/model dsl modem/router are you using?  Unless you are using a bridge modem (without router or configured to only bridge) you should not have to configure ppp on your computer.  And usually you cannot manually set IP address or gateway because those should be set automatically based on pppoe login, even if you have a static IP plan. The only things you would manually set are username and password for pppoe, and nameservers if you want something other than the automatic ones.

In WinXP what devices show having an IP address when you do **ipconfig /all** in a command window while internet is working?

---

### Post by larrymeditates on 2012-10-20
Thanks for the reply.  My router is a westell ADSL2+ and the 2 devices showing an IP address are the Ethernet adapter and PPP adapter.  

Since this post I went back and deleted the connections I had set up and used auto ethernet at which point an icon popped up saying a connection was established but firefox still gave the message that the server couldn't be found.

---

### Post by larrymeditates on 2012-10-21
Thanks for the reply.  My router is a westell ADSL2+ and the 2 devices  showing an IP address are the Ethernet adapter and PPP adapter.  

Since this post I went back and deleted the connections I had set up and  used auto ethernet at which point an icon popped up saying a connection  was established but firefox still gave the message that the server  couldn't be found.

---

