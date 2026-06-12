---
title: "iwconfig key not working"
date: 2010-03-03
forum: Networking &amp; Wireless
---

### Post by daweefolk on 2010-03-03
I use iwconfig to connect to my networks cuz i have fluxbox as my window manager. At home my network key is just a phone number and i can connect fine. at my college campus the key is "thinkofspring" and every time i do ```
sudo iwconfig wlan0 key thinkofspring
``` i get an error that the key is invalid or didn't work. Do i need to use a different command for full text keys? I'm running ubuntu 9.10

---

### Post by chili555 on 2010-03-03
Perhaps it is an ASCII key. Please try:```
sudo iwconfig wlan0 key [COLOR="DarkOrange"]s:[/COLOR]thinkofspring
```This is what *man iwconfig* says:> You can also enter the  key as an ASCII string by using the s: prefix.Another clue is that 13 characters is a valid ASCII key, but not HEX.

---

