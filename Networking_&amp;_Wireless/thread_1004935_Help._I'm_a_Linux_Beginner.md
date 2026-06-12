---
title: "Help. I'm a Linux Beginner"
date: 2008-12-07
forum: Networking &amp; Wireless
---

### Post by J_Boi on 2008-12-07
I've just installed ubuntu-8.10-desktop-i386 on my Acer Extensa 4620z and I'm having a little trouble with my wireless network adapter it's a Broadcom but I don't know exactly which version of it I have. I've right clicked the two screens in the upper right corner of the desktop and clicked wireless and also have clicked the add button.

I'm currently in the Editing Home part of the wireless and I've entered the SSID, Mode, Mac address and I've set the MTU to automatic. I don't have anything in the BSSID because unfortunately I don't know what that is. By the way I also have the connect automatically box checked.

I would love to get my wireless internet up and working on this so I can delve deeper into linux and ubuntu and see what's on the up and up.
Any help would be greatly appreciated.

---

### Post by Ayuthia on 2008-12-07
> **J_Boi said:**
> I've just installed ubuntu-8.10-desktop-i386 on my Acer Extensa 4620z and I'm having a little trouble with my wireless network adapter it's a Broadcom but I don't know exactly which version of it I have. I've right clicked the two screens in the upper right corner of the desktop and clicked wireless and also have clicked the add button.

I'm currently in the Editing Home part of the wireless and I've entered the SSID, Mode, Mac address and I've set the MTU to automatic. I don't have anything in the BSSID because unfortunately I don't know what that is. By the way I also have the connect automatically box checked.

I would love to get my wireless internet up and working on this so I can delve deeper into linux and ubuntu and see what's on the up and up.
Any help would be greatly appreciated.

To find out the make and model of your card, you will need to go into the Terminal and type:
```
lspci -nn
```Since you know it is a Broadcom card, you should be able to find it in the list.  

To activate the card (and you have a working internet connection in Ubuntu), you can go into System->Administration->Hardware Drivers and activate the Broadcom card there.  If you don't have a working connection, please post the results of lspci -nn for your wireless card and we can point you in the right direction.

---

### Post by J_Boi on 2008-12-07
> **Ayuthia said:**
> To find out the make and model of your card, you will need to go into the Terminal and type:
```
lspci -nn
```Since you know it is a Broadcom card, you should be able to find it in the list.  

To activate the card (and you have a working internet connection in Ubuntu), you can go into System->Administration->Hardware Drivers and activate the Broadcom card there.  If you don't have a working connection, please post the results of lspci -nn for your wireless card and we can point you in the right direction.

Thank you.
Ok. I found out that it's a Broadcom Corporation BCM4311 802.11b/g WLAN. What is the list that you were talking about??

---

### Post by Ayuthia on 2008-12-07
> **J_Boi said:**
> Thank you.
Ok. I found out that it's a Broadcom Corporation BCM4311 802.11b/g WLAN. What is the list that you were talking about??
Yes.  Since you have a 4311 card, there is most likely two options for you in Hardware Drivers.  The open source Broadcom b43 driver (which does require an internet connection to help make it work) and a proprietary Broadcom STA (wl) driver that does not require a working internet connection to make work.  It should not make a difference which one you choose. 

Hope that helps.

---

### Post by J_Boi on 2008-12-07
> **Ayuthia said:**
> Yes.  Since you have a 4311 card, there is most likely two options for you in Hardware Drivers.  The open source Broadcom b43 driver (which does require an internet connection to help make it work) and a proprietary Broadcom STA (wl) driver that does not require a working internet connection to make work.  It should not make a difference which one you choose. 

Hope that helps.

Ok. I installed both just in case. Is that bad.
The second one I installed said I had to restart, but the first one didn't. I haven't restarted yet but I'm hoping it works when I do. 
Yes. Thank you very much!

---

### Post by Ayuthia on 2008-12-07
> **J_Boi said:**
> Ok. I installed both just in case. Is that bad.
The second one I installed said I had to restart, but the first one didn't. I haven't restarted yet but I'm hoping it works when I do. 
Yes. Thank you very much!
It could be possible that the two drivers will conflict.  If you have already installed both, you might want to disable the Broadcom STA driver first.  

The Broadcom b43 driver does request a reboot because it needed to add the firmware portion for the driver.  The other did not need anything so it did not ask for the reboot.

---

### Post by J_Boi on 2008-12-07
> **Ayuthia said:**
> It could be possible that the two drivers will conflict.  If you have already installed both, you might want to disable the Broadcom STA driver first.  

The Broadcom b43 driver does request a reboot because it needed to add the firmware portion for the driver.  The other did not need anything so it did not ask for the reboot.

It works perfectly. Thank you so much for your help.!! Now it's time to do some digging around the forums to see what I can get into now that I have this installed and working!

---

