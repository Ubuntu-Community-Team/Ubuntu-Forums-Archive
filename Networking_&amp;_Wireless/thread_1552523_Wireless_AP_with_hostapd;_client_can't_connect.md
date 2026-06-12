---
title: "Wireless AP with hostapd; client can't connect"
date: 2010-08-13
forum: Networking &amp; Wireless
---

### Post by iverasp on 2010-08-13
EDIT: Never mind. My excuse is me being tired... Is there a way to delete whole topics?

Hello,

I'm attempting to make a wireless access point with my home server.  The card works fine and goes into managed mode (Atheros AR5008). I've configured hostapd to suit my configuration. My laptop sees the AP, connects, guesses the correct encryption and lets me write the password but after selecting connect (in NetworkManager) it just tries for a while and eventually gives up. The machines are currently only a meter apart. Heres the output of hostapd -dd /etc/hostapd/hostapd.conf:

---

