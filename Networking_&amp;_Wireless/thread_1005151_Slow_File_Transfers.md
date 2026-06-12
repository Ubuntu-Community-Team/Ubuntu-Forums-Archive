---
title: "Slow File Transfers"
date: 2008-12-08
forum: Networking &amp; Wireless
---

### Post by 67comet on 2008-12-08
I've got "several" Ubuntu machines in my house (4 servers (headless), 5 Desktops (Mythbuntu on 2). My network consists of Fiber from my ISP to my Vonage Linksys router to a 8 port hub and a WRT54GL running Tomato Linux (Image of my network) ([IMG]http://www.openlug.com/wp-content/uploads/2008/11/detailed-network-working.png[/IMG].

My problem is that my web server accepts file transfers from within my network very slowly. For example I tried to move a 300mb directory from my desktop (192.168.0.3) to my web server (192.168.0.2) via CLI (cp -Rv ~/Desktop/bigDirectory /media/web-server/website/images/location) and it took litterally 30 minutes+. So I zipped the directory and tried it the same way with similar results.

Where can I begin trouble shooting where the clog in my network is?

---

### Post by jmoorse on 2008-12-08
A few thoughts:

Are the PCs involved in either end of the xfer connected directly to the hub?

Check your interface stats for errors/etc: ifconfig -a

---

### Post by 67comet on 2010-09-10
Since this post; I've moved from Okinawa Japan to Misawa Japan and no longer have my beloved fiber connection. We're relegated to buggy, slow and very unreliable ADSL provided by Verizon Business.

I tossed all but one router (Unless you count the ISP's router). Purchased a Linksys 16 Port Switch and only manually manage 9 IP addresses. The Linksys WRT54GL handles all DHCP for wireless devices; secured with MAC address (It will hand out IP addresses for physically connected devices too if need be).

The network has been pretty much flawless since I installed the switch. I do want to add an N band router for some of my N enabled devices (Nexus One, Aspire One, MBP & iMac), but it still wouldn't help my PS3's occasional movie lag while streaming from my Movie server (Doesn't lag if I make sure nothing wireless is using the network for more than e-mail).

Here is a diagram of the current network. Working well; just debating on when to jump into upgrading my web server to 10.04 .. sigh .. 8.04 has been on there since 8.04 Beta and is basically flawless; except for Webmin (For Webalizer & MySQL Managment) keeps needing re-installed.

[IMG]http://www.openlug.com/wp-content/uploads/2008/11/detailed-network-2010.png[/IMG]

---

### Post by MaindotC on 2010-09-10
Dude you need to invest in Virtualbox man

---

