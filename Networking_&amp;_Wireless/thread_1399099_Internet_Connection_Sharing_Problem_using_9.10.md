---
title: "Internet Connection Sharing Problem using 9.10"
date: 2010-02-05
forum: Networking &amp; Wireless
---

### Post by willz06jw on 2010-02-05
Hi and thanks for your help,

I am using Ubuntu 9.10 and trying to use Internet Connection Sharing through my Dell Mini 9 laptop.

The incoming internet is from wireless
The outgoing internet is from Ethernet
I am using a crossover cable as I have heard this is necessary

I followed the 9.10 method on my Auto Eth 0 connection
[Here is a link to the Ubuntu Documentation I used]("https://help.ubuntu.com/community/Internet/ConnectionSharing")

The computer I am trying to share to does not pick up the internet being shared from the cable.

Any ideas?

Thanks again,
Will

---

### Post by Iowan on 2010-02-05
Can you ping the gateway machine (mini-9?) from the client?
Can client ping internet by IP address?

The client has an IP address? (**ifconfig -a)**

---

### Post by Yogotiss on 2010-02-05
Usually when setting eth0 to share, plugging both ends of the cable is all you have to do. If the guest machine isn't still online try reseting the cable connection on the host machine. Be sure that when you're disconnecting the cable from the host you get a message on the top right that says "Disconnected" then plug back in.

---

### Post by willz06jw on 2010-02-05
Did I have to use a crossover cable?  The tutorial didn't mention it.  Do I have to do anything to the wireless connection that receives the internet?

I will check the IP and ping when I get back home after work.

Thanks,
Will

---

### Post by Abhijit Navale on 2010-02-05
Crossover cable is best for ehternet.

Maybe this one is the reason, becuase it happend with me, so maybe with you, but be sure that the each single wire inside that cable is in its proper position, this wiki is useful:
[http://en.wikipedia.org/wiki/Ethernet_crossover_cable](http://en.wikipedia.org/wiki/Ethernet_crossover_cable)

I said maybe because previously I had vista, and in their help center they displayed crossover cable colors not matched with my actual cable.

---

### Post by Abhijit Navale on 2010-02-05
While reading this thread I had one question in mind that, 
Can I use eth as input internet and share my net using wlan as outgoing net?
Anyone have done this in real?

---

### Post by willz06jw on 2010-02-07
Abhijit, yes you can, it's called a wireless ad-hoc network

btw: I found out what my problem was.

The computer I was sharing to was a command line only install of ubuntu 9.10, and I needed to edit the interfaces file for me network.

Here is what I did to my command line only computer that the internet was going to (this is only for anyone else running a command line only system).

First I used nano to open my interfaces file
```
sudo nano /etc/network/interfaces
```
Then I made sure that my eth0 connection was set to dhcp (it wasn't listed when I started).  I added these lines to the bottom (don't add them if they are already there)
```
auto eth0
iface eth0 inet dhcp
```

I then restarted the network
```
sudo /etc/init.d/networking restart
```

then w3m and links started working perfectly (those are text only internet browsers for the uninitiated.

Have a good one guys and gals,
Will from Texas

---

### Post by Iowan on 2010-02-07
> **Abhijit Navale said:**
> While reading this thread I had one question in mind that, 
Can I use eth as input internet and share my net using wlan as outgoing net?
Anyone have done this in real?

[http://https://help.ubuntu.com/community/WifiDocs/ShareEthernetConnectionThroughWireless]("http://https://help.ubuntu.com/community/WifiDocs/ShareEthernetConnectionThroughWireless")

---

