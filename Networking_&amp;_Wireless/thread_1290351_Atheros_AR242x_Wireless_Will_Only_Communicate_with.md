---
title: "Atheros AR242x Wireless Will Only Communicate with Linksys Router"
date: 2009-10-13
forum: Networking &amp; Wireless
---

### Post by fattom23 on 2009-10-13
I have an Atheros AR242x wireless card in my Acer Aspire One 150, running Jaunty Netbook Remix.  I have the wireless working with the default drivers, but, oddly enough, the computer only wants to talk to Linksys routers.  I've successfully connected to about 4 different Linksys's (with solid data transfer rates on every connection).  However, any time I try to connect to a different brand router, I get unbearably slow connections.  Any ideas on where to look to try and solve the problem?  It's so strange to me that I don't even know where to begin.

---

### Post by fattom23 on 2009-10-21
Anybody out there got any ideas on where I can start with this?  Any ideas you have would be greatly appreciated.

---

### Post by fattom23 on 2009-12-09
As an update (and convenient bump to the thread), I uninstalled the network manager and installed wicd.  From my limited testing with one other brand of router (a dLink) everything seems to be working now.  Anyone got an idea of what it could be, so I can file a bug report?

---

### Post by linux6994 on 2009-12-10
To get you past your router you need the DNS address assigned by your ISP. You can go to your linksys and look under status and see what it is or the easiest and best way to run things behind your router is to run DHCP on your PC then the assingnments should get forwared to you PC from the router. 

Go to connection information via the network icon and see what your DNS and gateway are. You can even manually enter the DNS, Gateway and your IP address via the static entry and point the DNS and Gateway to the router such as 192.168.1.1 for instance and let the router do the fowarding back and forth.

Good Luck.

---

