---
title: "Change ip address of second internet sharing network card"
date: 2010-09-02
forum: Networking &amp; Wireless
---

### Post by Blue_Alien on 2010-09-02
I have a second network card in my ubuntu desktop that I have sharing my internet connection with a wireless router. I have set the router to a static ip address within the network cards range. But, every time I restart the computer, the network card uses a different ip address. One time it will be 10.42.43.1, the next time it will be 10.42.46.1, ect. This makes me have to hard reset my router every time it does this. How can I set the network card to use the same ip address all the time?

---

### Post by BkkBonanza on 2010-09-02
The **/etc/networking/interfaces** file stores the interface configs for system init. you will need to make sure it is set up correctly. **man interfaces** will give some info on that or you can post the file contents  here and we can suggest changes needed.

Also, if you are getting an IP address assigned on boot then it would appear your router is doing DHCP. If you choose to manually assign a static address make sure it is outside the range used for DHCP by your router. Better still don't change the network settings on your computer at all and just add a "**static lease**" in the router DHCP config to tell the router to always assign that IP value to your network card's MAC address.

---

### Post by Iowan on 2010-09-02
I'm also fond of the "static lease" method. Not as critical on a desktop, it lets laptops have a fixed address on one network, yet get a DHCP address elsewhere.

---

### Post by Blue_Alien on 2010-09-14
What I am trying to do is connect my internet connection to my desktop's main ethernet. Then I have a second ethernet card in my desktop which is connected to a wireless router running dd-wrt. The wireless router then allows my laptop and ps3 to connect to the web but, they cannot find my desktop on the network. How can I fix this?

---

### Post by Iowan on 2010-09-14
The second ethernet card should probably have a fixed address. [This]("https://help.ubuntu.com/community/Internet/ConnectionSharing") help page might be useful.

---

### Post by CharlesA on 2010-09-14
> **Blue_Alien said:**
> What I am trying to do is connect my internet connection to my desktop's main ethernet. Then I have a second ethernet card in my desktop which is connected to a wireless router running dd-wrt. The wireless router then allows my laptop and ps3 to connect to the web but, they cannot find my desktop on the network. How can I fix this?
Why not just hook up the wireless router directly to the internet and then hook up the machines to the router?

---

### Post by BkkBonanza on 2010-09-14
You are using your desktop machine as a gateway for your router. So you need to configure the router to treat it as a gateway. Alternately you can bridge the networks.

The router should have a static address set on it's upstream (usually to internet but in this case to your computer) port. It should not be set for DHCP unless you want to run a DHCP server on your computer (which doesn't make sense for a single client).

Then on your computer make sure the interface going to the router is configured for static in the /etc/network/interfaces file. If using Network Manager you will have to set it to not touch that interface or it will likely mess it up. That interface needs to be set to an IP in the same network as the router upstream port.

Then, to get traffic to go thru your computer from your router to your actual internet gateway you will need to either, 

1) enable forwarding, if you want these network segments to be separate (your LAN, router LAN), 

echo 1 > /proc/sys/net/ipv4/ip_forward

and add some routing rules, or 

2) configure the second ethernet interface as a bridge so that it acts like a switch on your LAN and keeps the router LAN on the same segment. This is much the same as just plugging the router into the same LAN as your desktop.

Or for simplicity you may be better off plugging your router directly into one of your LAN switch ports bypassing your system. It would then also not depend on your desktop being powered up for the second network to have internet access.

---

