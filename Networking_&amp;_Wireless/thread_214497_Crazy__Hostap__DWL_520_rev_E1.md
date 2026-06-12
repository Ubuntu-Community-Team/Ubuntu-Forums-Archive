---
title: "Crazy // Hostap // DWL 520 rev E1"
date: 2006-07-12
forum: Networking &amp; Wireless
---

### Post by greenwom on 2006-07-12
I've installed my D-Link DWL 520 rev E1 in my Dapper Box and had it up and running from the WIKI/Forum (I've used this card with Breezy with no probs)

The card uses hostap to load firmware.

So. I installed Samba on the machine and after reboot I lost my connection.  The odd thing is that the card wlan0 (with wifi0) apears when I run iwconfig but after I activate the card wlan0 disaprears????

I can't cut and paste the output of different commands but when I ran 
"dmesg | more"  I saw that there was some issue with firmware not being loaded?  I removed samba and reinstalled hostap.  Nothing works....

Where should I look next / what should I be looking for.

---

