---
title: "Does my wireless broadcast anything if I haven't connected to a network?"
date: 2012-06-26
forum: Networking &amp; Wireless
---

### Post by clay7 on 2012-06-26
Hello,

Does my wireless laptop broadcast any information BEFORE I select a wireless network to connect to (i.e., the computer name, MAC, OS), even if my wireless switch is on? If so, what is broadcasted?

---
Ubuntu 12.04 LTS, ath5k Atheros wireless card

---

### Post by asmoore82 on 2012-06-26
I don't think so. Some Other OS's that wish to fully support automatic connection to non-broadcasting or "hidden" networks have no choice but to constantly probe for the presence of them thereby leaking the very SSID that was attempted to be hidden.

Ubuntu remembers hidden networks by remembering their hardware's ESSID, which is basically the wireless access point's MAC address I think. So it can always passively be aware of when this "hidden" network is in range. Note that this scheme is slightly more secure but will have trouble with larger multi-access point "hidden" networks. You may have to manually join the hidden network from multiple locations on campus until all of the relevant ESSID's are learned.

---

