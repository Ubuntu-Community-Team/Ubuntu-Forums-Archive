---
title: "DNS keeps dropping off (12.04)"
date: 2013-09-01
forum: Networking &amp; Wireless
---

### Post by MarkJBrader on 2013-09-01
Ubuntu now fails to maintain DNS capability, as far as I can see. This began for me today.  We have a new router in the house, vastly better than the junk given to us by Comcast.  Every other machine (Windows, Apple, Roku) is very happy.   Also this machine with Ubuntu is my dual-boot.  The Win7 partition also loves the new router just fine.  So I do not think there is a hardware problem in the PC, nor do I think there is likely anything wrong with  the router config.

When I log in, the Network Manager says connected.  I bring up Firefox, and can go anywhere on the net, for between one and two minutes, then it fails to connect, unless I go restart the connection with the Network Manager.

I have tried the trick of taking out the dnsmasq entry for the Network Manager, and have changed from Auto DHCP to Auto DHCP addresses only, and put in my router.  Yes, the NM builds that address as a nameserver in /etc/resolv.conf, as I would expect.  Makes no difference.

Of course, I keep testing from a command window using "host [www.yahoo.com](www.yahoo.com) 192.168.10.1" and it always works just fine, even though apps like Firefox and the Ubuntu store cannot get through.  So the basic facility is just fine at the primitive command level.  I do not know where else to look.  Help.

Mark

---

### Post by MarkJBrader on 2013-09-01
Drat, 
   After all that, now the problem looks very different.  Now it looks like the wireless is dropping out at approximately one minute after startup.   Now on the tests I am starting a ping going to the router, then using Firefox.  Pings stop just as firefox does.

So the actual problem is that the wireless network keeps dropping off.  I am using a USB attached wireless from SMC, and have been for a long time, to support the dual-boot.

In do not know how to close this thread off.  I will start another if investigating at the driver level does not get things fixed.
Mark

---

### Post by SeijiSensei on 2013-09-01
Are you running a Bittorrent ciient?  If so, you should try reducing the number of simultaneous connections it uses.  (Note that is is different from a bandwidth cap.)  BT constructs lots of connections to the peers which can often overwhelm consumer routers and lead to the results you describe.

---

