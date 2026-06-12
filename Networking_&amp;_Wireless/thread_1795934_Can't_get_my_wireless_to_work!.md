---
title: "Can't get my wireless to work!"
date: 2011-07-03
forum: Networking &amp; Wireless
---

### Post by Ellie1523 on 2011-07-03
I changed from windows to ubuntu about a year and a half ago now. I have windows 7 still on my netbook. I can't connect to my wireless at all and I have to use the cable that you plug into the box. When i try and set up my wireless it asks for a SSID code, a BSSID code, a Device MAC address and a Cloned MAC address.<<What are these?! I don't know which code to put where. On my internet box it has a serial number, network name, wireless key and wireless PIN a BULK, MAC and Access Key. I am fed up now of not being able to get wireless. I am DESPERATE for help to get my wireless! Please someone help me!:sad:

---

### Post by chili555 on 2011-07-03
> When i try and set up my wireless it asks for a SSID code, a BSSID code, a Device MAC address and a Cloned MAC address.<<What are these?! I don't know which code to put where. You shouldn't need any of these! You should be able to click the Network Manager icon, see your network, click it and connect. If you have encryption, WPA and the like, you will be asked for the password and connect. Please see attached.

Do you see your network when you click the icon?

---

### Post by sandra mclean on 2011-07-03
Hello,
if it's a simple problem , then there are a series of good simple tutorials on youtube, i found them useful anyway,
 look for ubuntu tutorial videos.

---

### Post by Ellie1523 on 2011-08-04
No it doesn't. When I click on the network manager, under the wireless networks it says, >  device not ready (firmware missing) .

---

### Post by Ellie1523 on 2011-08-04
Do I need a less later version? I did have Windows 7 and when I got Ubuntu installed the style is all the same. I was thinking that could be a problem.

---

### Post by hausmusic on 2011-08-04
I actually had the same problem when I did this. What I did was connect it using the LAN cable and downloaded a firmware program through the software center, I can remember which one though but try and search firmware and see how it goes...

---

### Post by chili555 on 2011-08-04
> **Ellie1523 said:**
> No it doesn't. When I click on the network manager, under the wireless networks it says, .Let's see what you need. Please open a terminal and run:```
lspci -nn | grep 0280
```Many wireless cards, especially Broadcoms, require a firmware component to operate. The firmware must be downloaded separately. Post the result and we'll have you up and running soon.

---

