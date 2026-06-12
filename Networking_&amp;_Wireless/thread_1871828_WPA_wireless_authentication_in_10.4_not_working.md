---
title: "WPA wireless authentication in 10.4 not working"
date: 2011-10-29
forum: Networking &amp; Wireless
---

### Post by SOMDdan on 2011-10-29
I have three laptops, two with Ubuntu 10.4, and one with BT5. I also have two wireless access points, one a Cisco, and the other is a DDWRTGL. ALL THREE of my laptops will NOT connect to either WAP if WPA authentication is enabled. All laptops can detect my SSIDs, but all give a "bad password" when trying to connect. My ipad, on the other hand will connect to both WAPs effortlessly. The passwords I use on my laptops IS the same one used on the ipad; I entered the same exact password on all machines. This problem occurs whether I try to connect to the WAPs using NetworkManager or WICD. Beyond ensuring the password on my laptops is correct, I don't know what else to check or adjust to fix this. Any ideas?

---

### Post by garvinrick4 on 2011-10-29
If your ipad works with same password to your router then it has to be a setting you have
in network manager. You have multiple machines with same problem. I think you would
have to go over each setting til you find the culprit. Click on screenshots and compare:

---

### Post by garvinrick4 on 2011-10-29
Or is your router set to "N" only and you have "G" cards and ipad has an "N" card.
Check your cards out, will not recognize router and do exactly what you said if card
and router do not jive. Good place to look into code for Network card and driver below:
```
lspci -nnk | grep -iA2 network
```

---

