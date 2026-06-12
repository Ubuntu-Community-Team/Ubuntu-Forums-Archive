---
title: "Broadcom Wireless 4318 54g! HELP!"
date: 2006-06-26
forum: Networking &amp; Wireless
---

### Post by secretservgy on 2006-06-26
So, i have a 7510gx Gateway laptop with a Broadcom 4318 wireless chip. I researched the forums, and i found the article using fw-cutter and i did that and it turned my wireless light on, but it still dosnt connect or anything. How can i get it to work (in laments terms please :-) noob inside)

---

### Post by DarthMandeep on 2006-06-26
Could you run "iwconfig" in a terminal and post the output here?

iwconfig will show you what wireless cards are up and running on your system. Normally the wireless card will be called wlan0, and you can type "iwlist wlan0 scan" to see if your card can pickup any wireless access points in the area.

---

### Post by secretservgy on 2006-06-26
i actually just used  [this site ]("http://ubuntuforums.org/showpost.php?p=1105667&postcount=218")
now it works. thanks anyway..

---

