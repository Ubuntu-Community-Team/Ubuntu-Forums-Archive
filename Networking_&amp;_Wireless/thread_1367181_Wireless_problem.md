---
title: "Wireless problem"
date: 2009-12-29
forum: Networking &amp; Wireless
---

### Post by comewithme1717 on 2009-12-29
okay, now 

i have a huge problem that i really don't know how to solve....

(sorry if my english is bad, i'm from croatia)

now, i've installed the new ubuntu and now i can't connect to the internet wireless network... i searched for the informations in terminal and it says that *network is DISABLED, so it means that my wireless network adapter is DISABLED and how will i get it ENABLED, please help......

---

### Post by bkratz on 2009-12-29
> **comewithme1717 said:**
> okay, now 

i have a huge problem that i really don't know how to solve....

(sorry if my english is bad, i'm from croatia)

now, i've installed the new ubuntu and now i can't connect to the internet wireless network... i searched for the informations in terminal and it says that *network is DISABLED, so it means that my wireless network adapter is DISABLED and how will i get it ENABLED, please help......

Don't worry your English is fine. First, is the wireless adapter enabled in the bios and if so is there a switch on the keyboard (or keystroke combination for same) to turn it on?  If so we will have to determine the wireless adapter that you have with lspci or lsusb in the terminal (LSPCI or LSUSB in lowercase) and go from there.

---

### Post by comewithme1717 on 2009-12-29
can ypu describe me how to do that...?

---

### Post by comewithme1717 on 2009-12-29
wlan is enabled in windows but not in ubuntu how will i enable it in ubuntu

---

### Post by bkratz on 2009-12-29
> **comewithme1717 said:**
> wlan is enabled in windows but not in ubuntu how will i enable it in ubuntu



We still need to determine what type of wireless card you are using. Please go to the terminal
Applications>>Accessories>>Terminal
and type in the following commands one at a time and post the outputs back here using the code blocks (the # sign above) for ease of reading  use the exact (lowercase and uppercase below)

lspci -nn   (that is LSPCI in lowercase)
lsusb
lshw -C Network
sudo iwlist scan

This should give us an indication of the card type and condition

---

