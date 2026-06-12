---
title: "No wireless option on toolbar"
date: 2013-06-05
forum: Networking &amp; Wireless
---

### Post by jersan1 on 2013-06-05
This is like the 4th time I have been unable to get wireless. The toolbar at the top of the page usually has a section for wired networks and wireless networks. However, mine randomly will only show the wired networks tab and the wireless options won't come back no matter what I do. I've hit F2 but that wasn't it and I've looked at about every ubuntu help page for stuff like this that I could find. I always ended up having to reimage my computer. But I recently lost my disc and can't reimage it. Any idea? Need me to post results of commands or something?       
 Drop-down looks like this. No wireless.[ATTACH=CONFIG]243548[/ATTACH]

---

### Post by Annadin on 2013-06-05
it probably means your wireless network card is not supported, in terminal run sudo lshw -C network

then try and find your card here [https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

---

### Post by Cvxcvgg on 2013-06-05
Have you tried looking under Additional Drivers? With some NICs, you need to install a proprietary driver. My Broadcom is an example of this. Everytime I turn on my PC, I need to install the drivers, and then I can use my wireless. If that doesn't work, Annadin has the right idea.

---

### Post by jersan1 on 2013-06-05
If it was wireless network card wouldnt it have never worked? My computer worked fine for a while before I ever had this problem. According to the link I have  Realtek Semiconductor Co., Ltd. Device 8176 (rev 01) card. Can i fix this with a new driver or something or do i have to get a new card? (btw the card is internal not usb)

---

### Post by Cvxcvgg on 2013-06-05
It was the same for my Dell, worked fine until Ubuntu. I'm just saying it's a good first step before you go buy new parts.

---

### Post by jersan1 on 2013-06-05
Additional drivers fixed it. Apparently my driver was "Activated but not in use". I just deactivated it and reactivated it. All good. Thanks guys

---

