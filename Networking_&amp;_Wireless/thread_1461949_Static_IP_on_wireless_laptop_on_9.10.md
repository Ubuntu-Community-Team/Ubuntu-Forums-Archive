---
title: "Static IP on wireless laptop on 9.10"
date: 2010-04-24
forum: Networking &amp; Wireless
---

### Post by elbarto_87 on 2010-04-24
Hi All,

I have been googleing for the last hour and a half trying to find the easiest way to set up a static IP for my laptop's wireless connection.

The most promising link I found required me to delete the network manager but I do not want to do this as I often take my laptop with me so I need to be able to connect to new wlan easily. I just want a static IP so I can set up port forwarding.

Is there a equivalent process to windows XP where you just manually assign a local address like 192.168.2.9 or something like that? I tried setting it up through the network manager but later read that it doesn't work for encrypted connections.

I imagine there has to be a simple way to achieve this so I would appreciate any advice.

Thanks, Elbarto

---

### Post by mikewhatever on 2010-04-24
Gnome Network Manager has a very nice GUI for assigning static IPs, so deleting it would be unwise. Not sure what's the source of your info, but static IP has been working for years for me with wpa/wpa2.

---

### Post by elbarto_87 on 2010-04-25
Thank you very much!

I went back and continued to play around with the settings and it appears to work now. The page I was following had no mention of what to put in the DNS server field. I am surprised that all the information out there on how to do this is all listed in terminal commands when it is so easy to do from the network manager.

Thanks again,

Regards Elbarto

---

### Post by jarome on 2010-04-30
> **elbarto_87 said:**
> Thank you very much!

I went back and continued to play around with the settings and it appears to work now. The page I was following had no mention of what to put in the DNS server field. I am surprised that all the information out there on how to do this is all listed in terminal commands when it is so easy to do from the network manager.

Thanks again,

Regards Elbarto

Please tell me how you did it. What is the executable to run for Network Manager?

---

