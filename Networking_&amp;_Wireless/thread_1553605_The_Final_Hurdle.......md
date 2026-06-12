---
title: "The Final Hurdle......"
date: 2010-08-15
forum: Networking &amp; Wireless
---

### Post by DidYouReDo on 2010-08-15
I have resurrected a HP ze2355ea laptop using Ubuntu 9.10 Desktop, and after much reading of this forum (and not a little cursing and swearing) have successfully installed the drivers for the Broadcom 4318 onboard wireless card. As a result, the wireless is active and I can see local networks. However, when attempting to connect, I type in the WPA2 access key for my own router (a Netgear WGT624 v2) but am subjected to a 30 second pause, after which I am prompted for the access key again. This continues in a loop until I cancel the connection request.

All settings appear to be correct - Ubuntu correctly identifies the network SSID, the encryption type, and all settings including DHCP are set to automatic. I can connect easily via a Cat5 cable, and all other devices using my router have no connection issues. As a newcomer to Linux I am stuck - progress so far has been thanks to those on this forum who have posted their trials and tribulations with Broadcom network cards in the past!

All thoughts gratefully received!

---

### Post by DidYouReDo on 2010-08-15
OK, moving the goalposts slightly I have just updated (via cable) to 10.04 Lucid Lynx, and dabbled with installing wicd as suggested in a similar post.Sadly no change, I can still see 3 local wireless networks but can't connect to my own.....

---

### Post by DidYouReDo on 2010-08-18
Bump ):P

---

### Post by DidYouReDo on 2010-08-26
Well, nobody replied - not a sausage. Thanks to another forum I fixed it. Opened a terminal window and entered:

sudo aptitude remove network-manager
sudo /etc/init.d/wicd restart

then rebooted, opened wicd and it allowed me to connect to mywireless network.

Only a week of hassle to sort!

---

