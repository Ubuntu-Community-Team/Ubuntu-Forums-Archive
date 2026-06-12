---
title: "X60 wireless issue"
date: 2010-04-16
forum: Networking &amp; Wireless
---

### Post by paulstadler on 2010-04-16
Hi

i am new to Ubuntu and i recently got a X60 and installed Ubuntu 9.10 on it. I am not able to get the wireless working. I have a intel Pro (R) /Wireless 3945ABG wireless card.

any help would be great. 

-Paul

---

### Post by paulstadler on 2010-04-16
output of lspci -nn

02:00.0 Ethernet controller [0200]: Intel Corporation 82573L Gigabit Ethernet Controller [8086:109a]
03:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4227] (rev 02)


------------------------------------

---

### Post by paulstadler on 2010-04-17
Any help? i am not able figure this out.

---

### Post by lostjohn on 2010-04-17
Try this goto administration/network tools/ look in the drop down for wireless interface (wlan o) or try loopback interface (|o) it work on my belkin wireless card.

---

### Post by paulstadler on 2010-04-17
Hi lostjohn

is there anything that i need to look for in these dropdowns? i use Belkin as well. in the network manager i can see all other wireless connections, but when i connect, i never connects. 

I use WPA-PSK .

thanks
-P

---

### Post by bkratz on 2010-04-17
> **paulstadler said:**
> Hi lostjohn

is there anything that i need to look for in these dropdowns? i use Belkin as well. in the network manager i can see all other wireless connections, but when i connect, i never connects. 

I use WPA-PSK .

thanks
-P

Here is a two page thread on your card and wpa connections.

[http://ubuntuforums.org/showthread.php?t=1421783&highlight=3945ABG](http://ubuntuforums.org/showthread.php?t=1421783&highlight=3945ABG)

The last posting says he solved it and how. It may not help, but who knows?  Your's starts in post 12.

---

### Post by lostjohn on 2010-04-17
go here this may help  [https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

---

### Post by paulstadler on 2010-04-18
Thank you all.

I was able to fix this. i had the SSID as non broadcast. once i changed to broadcast i was able to connect to it.

once i connected, i again enabled the non-broadcast and it was working fine.

---

