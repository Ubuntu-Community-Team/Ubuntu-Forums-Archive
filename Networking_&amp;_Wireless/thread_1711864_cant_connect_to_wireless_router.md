---
title: "cant connect to wireless router"
date: 2011-03-21
forum: Networking &amp; Wireless
---

### Post by MentatGhola on 2011-03-21
Ive got a linksys befw11s4 and I'm running 10.04 on my desktop.  I booted and logged into the router no problems first try.  After a few minutes I got kicked and haven't been able to re-log even after multiple reboots, router resets and dhcp renews.

I used to periodically get kicked when I was running different versions of ubuntu 9 but I could always relog every 20-30 mins (somewhat random intervals actually) so although annoying I could deal with a similar problem with a routine click.  Not anymore in 10.04.

Please give advice.

---

### Post by cipherboy_loc on 2011-03-21
Try getting to/checking the logs on the router. Also, is there MAC Address filtering? What type of router is it?

---

### Post by arvevans on 2011-03-21
While I'm not an expert on your linksys befw11s4 router, there are some things that you can look at.  I'm making the assumption that when you say you are getting dropped, it is dropping you from the WiFi link, and not from the wired administrative link connection?

If you have your WiFi router set to operate on the same channel as some other WiFi router in the same area, it could be that the other system is blocking your signal, or at least confusing it enough that packet errors are causing your connection to drop out.  If this is the case, log into your router using a wired (not WiFi) connection and change channels.  Then go back to your Wi-Fi connected device and re-establish the WiFi connection.  

There are many things that operate on the same frequencies as WiFi equipment.  In the USA, WiFi is licensed for these frequencies as "Secondary Users".  The FCC licensed "Primary Users" have absolute control over their access and you are not allowed to cause interference to them.  

Other things like Microwave ovens, cordless telephones, Intercoms (Baby Monitors, etc.) and radar equipment also operate on the same frequency as WiFi devices.  Some have much more power than your WiFi unit and thus can block your signals.  Changing channels on your WiFi hub/router can usually provide a way to work around other users of the frequency.

If you suspect an interfering signal problem, you might want to do a "scan" of WiFi devices in your area (do it from your lap top) to see what other WiFi devices are in your area and what channel they are operating on.  If you and someone else are on the same channel, one of you may have to switch channels.

---

### Post by MentatGhola on 2011-03-21
Correct the admin hardwire is an xp desktop.  I should be more specific:  The wireless connection registers in the network list but I can't pass authentication even though the wep passphrase is correct.  On first boot in a couple months authentication was successful but after a few minutes connection terminated.

Laptop running windows 7 is connected wireless.  Also there is another windows 7 laptop that has no problems connecting wireless.  I will see about changing channels even though that is probably not the problem as the windows computers are connecting.

---

### Post by MentatGhola on 2011-05-09
Still having the same problem if anyone has any ideas.

---

### Post by josephmills on 2011-05-09
hi there fancy router 
[http://cavemonkey50.com/2005/12/install-hacked-linksys-firmware/](http://cavemonkey50.com/2005/12/install-hacked-linksys-firmware/)
[http://www.youtube.com/watch?v=YJ4c_FxVQBc](http://www.youtube.com/watch?v=YJ4c_FxVQBc)

---

### Post by MentatGhola on 2011-05-10
Ok.  I thought that might be the problem.  I just checked out that dd-wrt.com database and it says support is not possible.  Guess I need to shell out some tickets.  

Interestingly I was able to connect briefly.  I wonder why that would be.  When did this dd-wrt stuff come about?  I was able to connect in 9.x

---

### Post by josephmills on 2011-05-10
not sure how long it has been around also have you tred this [http://homesupport.cisco.com/en-us/wireless/lbc/BEFW11S4](http://homesupport.cisco.com/en-us/wireless/lbc/BEFW11S4)

---

