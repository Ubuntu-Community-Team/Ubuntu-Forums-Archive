---
title: "Odd Wireless problem"
date: 2011-03-14
forum: Networking &amp; Wireless
---

### Post by bluepinktriangle on 2011-03-14
Hi Everyone, 

This is my first post on here, but i have been messing about with ubuntu for a couple of years now on and off. 

i just brought myself an Archos 9 tablet and im currentyl duel booting with Windows 7.  I have managed to get everything running with ubuntu (albeit after 6hrs) my wireless adapter (Broadcom BCM4311) seems to be working fine. that is untill i actualy want to connect to the router, i can select the router and it will spend maybe 20 seconds trying to connect and then just gives in and says connecting failed.  I was pretty sure it was a router issue so i have looked through and checked everything twice. i can connect with my phone, PC, PS3 ect ect. Anyway i was doing some sniffing around the gconf-editor and noticed that the auto connect setting stored thier was wrong, it had the encryption down as WPA-PSK and not WPA2-PSK which is what the router is using. So i changed it and voula it worked.

That is until i rebooted, but it didnt change the setting. it copied the settings and changed the copied one, and once again no wireless. 

So im just wondering if i am missing something completly, or it really is just choosing the settings that dont work. 

Does anyone have any idea on how to fix it? 

Sorry about the post being so long. 


Chris.

---

