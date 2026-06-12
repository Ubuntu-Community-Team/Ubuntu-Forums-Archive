---
title: "LAN management GUI?"
date: 2010-06-09
forum: Networking &amp; Wireless
---

### Post by Taliesin77 on 2010-06-09
Hi all, this is my first post in the forums.  I've been using Ubuntu since 2006, and love it!  I've even gotten a few others hooked when their Windows machines crapped out due to viruses or other problems.  And Ubuntu has only gotten better.
 
Now I'm trying to build a home network around a wireless router (Linksys).  I'm set up with a desktop wired to the router, and two laptops regularly connect wirelessly.  The wireless router is connected to a cable modem.  Everything works fine (except getting the Ubuntu laptop to connect wirelessly using WPA).
 
What I would like to do is use the desktop as a server, so I can see who is connected at any given time, control security protocol, edit the MAC address list, boot off unwanted users, etc.  I can do most of this by connecting to 192.168.1.1, but would prefer something on the desktop.
 
Looking through the Software Center, the only thing I can find is KontrolPack.  Anyone use this?  Will this give me the functions I want?
 
Thanks!

---

### Post by Taliesin77 on 2010-06-10
I'm going to try Skipole to monitor the LAN and TFTPGui to configure the router how I want -- if you can configure a Linksys/Cisco wireless router like an enterprise router.
 
I'm a CCNA, but have never tried to configure a Cisco device from Ubuntu, and I've only used the FTP (web browser) interface on the Linksys/Cisco wireless router at home.

---

### Post by lz1dsb on 2010-06-10
Configuring a Cisco router or any router doesn't really matter from the OS you're using. You just need a terminal client to access the device. In the case of Lynksys (I'm assuming you're using the default firmware) you need a browser. 
I don't really understand what you're trying to do. You want to have a desktop PC where you can monitor the whole LAN traffic from. Is that correct? But in this case the access is controlled by the router, so you can only monitor the LAN access and traffic from the router. Either using snmp, or over http. Or maybe I don't get at all your idea?

Cheers,
Boyan

---

