---
title: "WPA2-protected wireless, got disconnected, shows up as WEP-protected afterwards"
date: 2013-03-23
forum: Networking &amp; Wireless
---

### Post by veroslav on 2013-03-23
Hi,

last week I brought my work laptop (Windows 7) home and tried to connect it to my home wireless network. The router is a D-Link DIR-615 and I use a WPA2 protection. I had my desktop (Ubuntu 12.04) already connected when I tried connecting the work laptop.

Shortly after the laptop tried connecting, it failed and simply said it couldn't connect. I tried once again with the same outcome. However, I also noticed that my desktop got disconnected in the process as well. It asked for my password so I entered it but it wouldn't connect. I tried a few more times but without success.

What was most interesting is that suddenly Ubuntu saw my wireless connection as WEP-protected! I also checked work laptop and it also saw the connection as WEP-protected! Obviously I was not gonna manage to connect now as my WPA2-password is much longer that the maximum WEP-password length I was being asked for now.

I didn't understand anything so I logged on to the router and verified that the connection settings were the same as before (WPA2). It was, I couldn't see anything funny in there.

I rebooted the desktop, booted into Windows 7 and Kubuntu 12.10 (on other partitions) and same thing there: the connection was seen as WEP.

At this point the only thing that helped was to reset the router to the factory settings and changing BSSID to something new. Now I finally could connect.

From now on I was convinced it had to do something with the work laptop that it somehow screwed up my wireless while it tried to connect to it.

However, today I got disconnected again from my desktop whilst in the middle of some heavy downloading. Again, after disconnection, the wireless appears as WEP-protected and I am unabled to connect!

I tried everything, even resetting the router but for some reason I am still getting the WEP-protection even though I set it to WPA2 after factory reset.

I am completely clueless and would appreciate any explanation as to what really happened here and how I could avoid it in the future. I never had any such problems since I bought this router 2 years ago. Also, been using the Ubuntu 12.04 installation since April 2012 without any issues.

Thank you in advance.

Kind Regards,
Veroslav

---

### Post by veroslav on 2013-03-25
Bump

---

