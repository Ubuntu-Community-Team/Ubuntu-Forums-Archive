---
title: "Proper Connection Settings to connect to Internet"
date: 2009-12-25
forum: Networking &amp; Wireless
---

### Post by dan9077 on 2009-12-25
I cannot connect to the internet. I'm using Ubuntu 9.10 and running from the CD. I have a 2 Wire 1000HW DSL modem. I am connecting at home, through my 2wire router, and do not need to set up a corporate network. The results from typing sudo dhclient say "No DHCPOFFERS received." I don't know what this means.   

_[[IMG]http://img695.imageshack.us/img695/1271/ubuntuscreenshot1.jpg[/IMG]]("http://img695.imageshack.us/i/ubuntuscreenshot1.jpg/") _


[[IMG]http://img189.imageshack.us/img189/1728/ubuntuscreenshot2.jpg[/IMG]]("http://img189.imageshack.us/i/ubuntuscreenshot2.jpg/")

What do I do? How do I configure my connection?[URL="http://img189.imageshack.us/i/ubuntuscreenshot2.jpg/"]
[/URL]

---

### Post by chewearn on 2009-12-25
"No DHCPOFFERS received." means your computer is not getting an IP address from the router.  Is your router's DHCP server properly set-up?

---

### Post by dan9077 on 2009-12-25
> **chewearn said:**
> "No DHCPOFFERS received." means your computer is not getting an IP address from the router.  Is your router's DHCP server properly set-up?

When the Ubuntu CD is not in the computer, XP connects to the internet just fine. My router shows all 3 lights lit green (power, broadband link, local network). I don't have to do anything to make it connect. I'm just automatically on the internet. Even after I reformat my hard drive I am on the internet immediately without having to do anything. 

If that means my router's dhcp server is properly set up, then yes. 

Is there something else I can do?

Once I put in the ubuntu CD and run it, the broadband and local network lights go out. When I type sudo dhclient (and get no DHCPOFFERS received)  those two lights are off.

---

### Post by chewearn on 2009-12-25
I am not entirely positive since I don't have the said 2Wire router.

Perhaps you could:
1. unplug the ethernet cable
2. then a router reboot (this will clear the DHCP assignment table)
3. wait a minute or two for the router to get back up
4. then plug back the cable again, wait while network manager request a new IP.

---

### Post by Iowan on 2009-12-25
I suspect [this]("http://ubuntuforums.org/showthread.php?t=1156441") thread has run it's useful route, but just in case it helps...

---

