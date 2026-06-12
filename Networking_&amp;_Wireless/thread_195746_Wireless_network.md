---
title: "Wireless network"
date: 2006-06-13
forum: Networking &amp; Wireless
---

### Post by jitesh on 2006-06-13
Tried to setup a wireless connection, the wireless network card is setup but I can't connect on it, I set the default gateway to use  "wlan0"  but it goes back to my wired eternet connection "eth0". When I deactivate the "eth0", i can't set the default gateway to "wlan0" What did I do wrong?

---

### Post by mandragor on 2006-06-13
Can you paste the contents of your /etc/network/interfaces ?
What I have done earlier is to just comment-out all lines that refer to eth0 to
deactivate it, if wlan0 is connected to the Internet your machine should use it.

---

