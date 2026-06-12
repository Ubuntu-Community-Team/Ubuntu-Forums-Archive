---
title: "Ethernet to wireless Access point error"
date: 2009-03-24
forum: Networking &amp; Wireless
---

### Post by jimma on 2009-03-24
I've just bought a DWL-2100 access point. I've set it to wireless client mode and then connected it to a wireless router in another part of my house. I then have a ethernet cable to my computer. When running Win XP I get a IP address and can browser the web. When using ubuntu it cannot get an IP address? I cant figure out why it wont work. It should see the access point as a standard ethernet connection?!?!

I've tried using a static ip but that also failed. Any help would be greatly appreciated.

---

### Post by jimma on 2009-03-25
bump...

---

### Post by lisati on 2009-03-25
Are you able to log into the device's configuration page at all?

EDIT: You should be able to go to the device's configuration page by opening a browser and typing in ```
http://192.168.0.50
``` into the address bar

---

### Post by jimma on 2009-03-25
I cant get into the configuration page either. It has a different subnet mask. The gateway is set at 0.0.0.0 on the D-Link should I set it to something?

---

### Post by jimma on 2009-03-26
bump

---

### Post by BkkBonanza on 2009-03-26
Yes, set the gateway to the machine/router that gets you out to the net. It probably doesn't know where to go to get dhcp. I had a similar setup using my Linksys router with dd-wrt. Worked nicely. But there are a lot of options that you have to get right or things won't fly.

---

### Post by jimma on 2009-03-26
How do I just add the gateway. In NetworkManager I have to add a ip and a subnet mask as well. I tried copying all the details from my WinXP network config into my Ubuntu but I still get nothing. 

Its quite frustrating as my WinXp and my Asus Express Gate both connect using no config just via DHCP why does Ubuntu not connect...

---

### Post by jimma on 2009-03-26
bump again :-)

---

