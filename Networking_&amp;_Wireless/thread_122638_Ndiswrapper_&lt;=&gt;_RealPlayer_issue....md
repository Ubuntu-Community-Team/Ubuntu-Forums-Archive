---
title: "Ndiswrapper &lt;=&gt; RealPlayer issue..."
date: 2006-01-28
forum: Networking &amp; Wireless
---

### Post by hajk on 2006-01-28
I have a SpeedTouch 121g USB wireless dongle, for which I have the latest
Windows BT4501G driver (dated January 2006) installed in the ndiswrapper package that comes with Breezy. The setup works fine until I try to get a
stream going in RealPlayer (the latest package from the Marillat sarge
repository): the connection thingy goes wild, the connection is never made, and 
after stopping RealPlayer the wireless connection itself is also lost. I can only
restart by doing a 

sudo rmmod ndiswrapper
sudo modprobe ndiswrapper
sudo ifup wlan0

routine. The last command complains about an already existing lock file, but 
does re-establish the wireless connection. 

There is no such problem with another computer in the same network using
a NetGear WG511T card with the madwifi module. 

So, it would appear that the problem is with ndiswrapper -- does anybody 
have any idea as to what's wrong?

---

