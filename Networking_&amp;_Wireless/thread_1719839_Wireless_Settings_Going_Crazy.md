---
title: "Wireless Settings Going Crazy?"
date: 2011-04-02
forum: Networking &amp; Wireless
---

### Post by goob1284 on 2011-04-02
Hello, this is my first post on this website and yes, i am new to Ubuntu. Usually, I could figure things out on my own, but this goes beyond me. I stayed up to 2 last night trying to get my wireless card to work and just couldnt. I did install the drivers via ndiswrapper and they are there (ndiwrapper -l i believe). Now, i am trying to connect to 2WIRE398 which is most certainly my home network, and the WEP key is 4098298391 because i have my cell phone right here which is connected to it, and when i had windows 7 it also worked. The main problem is, when i try to connect to it, it finds the network, but it only says WPA Personal under security. I tried clicking on it but thats the only one available. When i click on another random connection in my neighborhood, WEP is an option. I have no idea what is going on. I tried making a new connection and that didnt work. I even tried changing the settings on the network in the network settings to wireless security to WEP but it always changes back to WPA. Please help thank you.

---

### Post by goob1284 on 2011-04-08
Please help. i would like to get this up and running ASAP.

---

### Post by chili555 on 2011-04-08
How about showing us:```
sudo iwlist wlan0 scan
ndiswrapper -l
```Thanks.

---

