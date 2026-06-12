---
title: "Wireless card not recognizing some ssids"
date: 2006-03-13
forum: Networking &amp; Wireless
---

### Post by IKoDiaKI on 2006-03-13
I have a BCM4306 (rev 2) wireless card.  It works fine with the bcmwl5 drivers, installed with ndiswrapper, except when I am on campus. When i do iwlist wlan0 scan all of the information about the routers will show up but essid = "" for everyone of them. I think it has something to do with multiple networks with the same ssid but im not sure. Why are they not showing up? Is there anything i can do to fix it? Any help would be greatly appreciated.

---

### Post by IKoDiaKI on 2006-03-14
No one has an idea of what might be causing this to happen?

---

### Post by javaTard on 2006-03-17
I had this issue as well with my HP zv5000 running the 64bit Ubuntu. Something to do with the repeaters at my college. I have however fixed it, but having it been so many edits of files, I do not remember what did it for me.

---

### Post by IKoDiaKI on 2006-03-27
Alright, I found out that they are using a hidden ssid on campus. So, has anyone had any success in connecting to hidden ssid's with the bcm4306? I've tried not putting in anything for the ssid and just putting in the WEP key and still nothing.  Hope someone can help me, this is getting really frustrating.

---

### Post by polo_step on 2006-03-29
[FONT="Fixedsys"]I don't know what chip this device uses, but I have discovered that some chips simply do not recognize hidden SSIDs, even with the OEM drivers and utilities in an XP system.  Why, I dunno.[/FONT]

---

### Post by jml on 2006-03-29
Have you tried to get specify the SSID you campus network is using, rather than scanning for it?  Will they give you that information?  If they don't, another option might be to try running Kismet, a wireless netwok sniffer, and see if you can determine the SSID and then configure your card.

---

### Post by IKoDiaKI on 2006-04-04
I'll give it a shot. Thanks for the help.

---

### Post by IKoDiaKI on 2006-04-04
Oh yeah, I meant to say that I have tried to specify the SSID and I can talk to the unix administrator in our cp sc department... he might be able to help. Thanks again.

---

### Post by IKoDiaKI on 2006-04-12
Well I tried talking to my network administator and kismet, neither worked. Kismet would not working with any cards that use ndiswrapper. Any other ideas?

---

### Post by byrdmeln on 2006-04-12
I have the same chip on my belkin 7010 and use the same driver.  There seems to be some sort of bug with the drivers as it won't allow scanning (at least without crapping out) and won't report signal strength from what I can tell.  (unless I really am at 100% to my home network no matter where I drive around in the city)

However, my home network has both wep and is hidden, and I can connect fine.  

The card doesn't seem to like using any of the fancy network managers that come with ubuntu or any of the optional downloads ...just the good old networking applet.  As a matter of fact, my card would NOT work with any of those fancy networking manager things.  But it will with System-Admin-Networking ...open it, click on your card, hit properties ...type in the actual name of the hidden network (case is important) ...type in the wep if one is used (case shouldn't be important but it appears to be as caps wont' work on my computer, only small case)  then hit ok, hit activate, hit ok again.  

You might have to turn off the connection type and turn it back on again (in the networking applet) a few times to get the dang card to connect ...once it does then logout (saving current setup) then log back in and see if it works.

Do you actually need to do all this?  I have no idea, it's just what works for me when I want to change wireless networks.  :rolleyes: 

I do keep wifi-radar on my machine, and I'll occasionally open it up to find a network ...it will report unhidden networks ... I just won't be able to connect to them with wifi-radar active ...so I have to load it up, run it, write down names of networks, then unload wifi-radar and reboot.  Much fun!

---

