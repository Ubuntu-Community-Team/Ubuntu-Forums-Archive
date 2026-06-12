---
title: "wpa2 hex key"
date: 2009-06-13
forum: Networking &amp; Wireless
---

### Post by dutow on 2009-06-13
Helo

I have a wpa2 wireless network with a hex key (64 characters). It works from windows without problems, but not under linux. I tried the default network-manager and wcid on 2 computers with ubuntu.

Is it possible? How can I connect to this network?

---

### Post by chadk5utc on 2009-06-13
need a bit more info??
what OS are you using now?
What wireless card are you using?
What chipset is your wireless card?

---

### Post by dutow on 2009-06-13
I'm using Windows 7 (wireless work) and ubuntu 9.04 (works with alphabetical keys)

RT2860 chipset.

iwlist ra0 scan works, I can see wireless networks, and I can connect to WPA2-PSK networks using smaller keys (like "asdfasdf", etc), but not to networks using 64 bit hexadecimal keys. Same on another laptop (with ubuntu 9).

wicd.log stopes with "authentication may have failed" after pages of "WPA CLI RESULT IS SCANNING / ASSOCIATING / SCANNING" messages.

---

### Post by chadk5utc on 2009-06-15
just found an entire thread for this [http://ubuntuforums.org/search.php?searchid=60602044](http://ubuntuforums.org/search.php?searchid=60602044)  try here

---

