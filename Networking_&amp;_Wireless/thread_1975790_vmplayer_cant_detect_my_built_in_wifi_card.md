---
title: "vmplayer cant detect my built in wifi card"
date: 2012-05-07
forum: Networking &amp; Wireless
---

### Post by ferdinanm on 2012-05-07
hi everybody,
i´m trying to use backtrack 3 and 4 on my windows 7 pc. whenever i´m trying to boot backtrack 3 the software detects my built in card (atheros ar9285 802.11b/g/n wifi adapter), but it is deactivated and can only be activated when i´m running windows 7. and when i´m using vmplayer workstation on windows 7 it doesn´t detect the wifi card.
what do i have to do to enable the wifi card while booting backtrack? and how can i use my built in wifi card on wmplayer workstation?
any suggestions are welcomed. thank you

---

### Post by tilt2kngiht on 2012-05-07
In VirtualBox there should be some icons at the bottom right. If it's connected it should be under the USB devices, click it so there's a check mark next to it.  If you booted it goo to the terminal and enter "ifconfig" to see what wlan port it's in wlan0 wlan1 wlan2 (mine was wlan1) then enter "ifconfig wlan1 up". Close terminal. Then go to the Applications-Interntet-Wicd Network Manager and select your network. Open properties-enter the password then close out and click connect. Spoon fed enough? 
:lolflag:

---

### Post by ferdinanm on 2012-05-08
thank you for your quick response. i switched to a usb wifi card and now everything is fine. but i´m having problems with backtrack. i cant get a wpa handshake. i have collected a lot of packages (more then 6000) but the power is low (23). has it something to do with the power? do i need to be closer?

---

### Post by tilt2kngiht on 2012-05-08
I wish I could help. I just started with backtrack and I'm having trouble recovering my Windows partition. Bad install #-o

---

### Post by ferdinanm on 2012-05-09
good luck with that, hope everything works out for you.  thank you for your help, greetings

---

