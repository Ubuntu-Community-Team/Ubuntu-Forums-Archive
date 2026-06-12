---
title: "Knetworkmanager keeps asking for router password"
date: 2011-03-08
forum: Networking &amp; Wireless
---

### Post by tarahmarie on 2011-03-08
This happens all the time. I have a Vizio router, I run Kubuntu 10.10, I set my Kwallet password to blank, but Knetworkmanager keeps asking for the router password (WPA2, 10 digit random). I tried Wicd as well; both of them have the same problem.

What am I doing wrong?

---

### Post by ankspo71 on 2011-03-08
Hi,
Have you already tried telling knetworkmanager to store your "Connection Secrets" (your wireless password) in an unencrypted file? This will stop kwallet from asking for your password. 

If you want to try it, Right click on your knetworkmanager icon in your panel, click on Network Manager Settings, then when the Network Manger Settings window opens, Click on "Other", then for Connection Secrets choose to store them "in file (unencrypted)". If I remember correctly, it will ask you for your password one last time.

I'm not sure how wicd handles passwords though.
Hope this helps.

---

### Post by tarahmarie on 2011-03-08
> **ankspo71 said:**
> Hi,
Have you already tried telling knetworkmanager to store your "Connection Secrets" (your wireless password) in an unencrypted file? This will stop kwallet from asking for your password. 


Yes, this is actually one of the first things I tried. Thanks though. Any other ideas?

---

### Post by tarahmarie on 2011-03-10
bump

Notably, sometimes it helps to delete my wifi connection and recreate it. It will sometimes restore my service, but soon it will disconnect and keep bugging me for the router password again.

---

