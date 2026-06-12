---
title: "Sharing and Internet connection via Aircard"
date: 2009-05-22
forum: Networking &amp; Wireless
---

### Post by Musicologynut85 on 2009-05-22
My grandparents live out in rural nowhere, and so they bought an AT&T aircard to get away from AOL dial-up (no DSL/Cable out here).

They have two desktop computers, both of which run Jaunty; and they want me to set up the computers so that they can share a connection off the air-card. I've been trying to get it to work, but I have no clue how to go about this. I have a wireless router and one of the computers has a wireless card in it.

Suggestions?

Oh, the computer without the wireless card is currently dual-booting with Windows XP.

My plan was to plug the air-card into the computer without the wireless, and then run the router out of that computer. From there, I was going to use the wireless router to broadcast the internet connection to the second computer... that has yet to pan out.  

The router is a LinkSys WRT54GS2.

Thanks!

-Jeff

---

### Post by superprash2003 on 2009-05-23
yea.. your approach is correct.. you would need ICS for this , a simple way to do this , is by installing firestarter if not you could do it manually [http://www.prash-babu.com/2009/02/internet-connection-sharing-in-ubuntu.html](http://www.prash-babu.com/2009/02/internet-connection-sharing-in-ubuntu.html) .. you should disable DHCP server in your linksys.. connect a LAN cable form your pc to the LAN port of linksys ( not WAN ) . then you could set up static ip on both the machines .. ( DHCP not required )

---

