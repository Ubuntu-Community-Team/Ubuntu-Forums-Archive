---
title: "Getting a Wireless Connection at Startup"
date: 2006-04-22
forum: Networking &amp; Wireless
---

### Post by andyj144 on 2006-04-22
I recently put ubuntu on my laptop, and I generally like it.  The problem I'm having is small, but irksome. 

I am a student, and take my laptop back and forth between home and school almost every day.  The wireless card works fine in both places, but if I shut down in one location, and boot back up in the other, the system won't detect the wireless network in the new location during start up.  As a result it just sits there for about minute while it try's to configure the network connection during the boot procedure.  Then I have to manually tell it where I am after logging in .  (I have the settings for both networks saved as locations in the "Networking" utility).  If I shut down and restart in the same location, it makes the connection right way and the boot goes quickly.

Is there a way to make the system connect to any one of several preconfigured connections during startup, depending on whats available (i.e. like XP does).  If not, is there a way to shorten the timeout delay to speed up the boot.  

Thanks
Andy

---

### Post by PhilOSparta on 2006-04-25
I have this same problem when traveling.  Since every hotel has a different wireless connection, Ubuntu trys to sync into my home connection.  When it can't find the home connection, I have to go into the network menu as you describe.

I haven't found the solution either, but you can speed up the boot by hitting ctrl-C when you see the network functions during the boot.  The second time is when the system trys to access the time server at Ubuntu.  It would be nice if the boot process would not try to access the time server if there was no connection.

It would be nice to see this fixed in the future.

---

### Post by jml on 2006-04-25
I found this posting after searching the forums for "boot profiles"  Hope it helps.  Joe

Hi Matt,
I had a similar situation. I installed Wifi-radar, and that does a "nicer" job (I think) of creating preferred wifi network profiles than the Networking tool. Even though I created different Locations in the network tool, I still had to switch them manually from home and work. Once I created a profile for home and work in Wifi-radar, my IBM R51 connects at boot automatically, wherever I'm at. At home, I use WEP, and at work (a public high school), it's an unsecured wireless network. Wifi-radar can manage both secure and unsecure wireless. It also has a WPA section, but since I don't use WPA, I'm not sure if it works well.

---

