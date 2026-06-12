---
title: "Internal Broadcom Card fails but ..."
date: 2009-01-14
forum: Networking &amp; Wireless
---

### Post by saywot on 2009-01-14
For a few weeks I have been happily running Ubuntu 8.10 connected to my home network with the internal Broadcom card in this Dell Latitude laptop. I took the laptop away for a week and can now no longer connect to the usual network in the usual way. This evening I inserted a PCMCIA wireless card and the Atheros drivers for it installed automatically and faultlessly.
I did an update, downloaded all my eMail and then decided to re-boot as requested by the update manager. I disabled the Atheros drivers and removed the card and did the re-boot and the internal card won't re-start (even though the LED on the laptop says that the card is functioning/running)

How might I start the internal chip so I don't need to carry around yet another device in order to use this portable PC - the more I have to tote the less portable it becomes:confused:

---

### Post by Ayuthia on 2009-01-14
Are you able to scan for any wireless sites with the Broadcom card or using anything in /etc/network/interfaces?

---

### Post by saywot on 2009-01-14
No

But there's some flaw in NetworkManager that keeps changing the the pairing in the Netwoking config files, I only need/want/can use TKIP but it keeps reverting to TKIP CCMP and then my router won't accept any handshakes and just turns it's back on me and will ignore me for the rest of the night.

If I edit the config file and remove ccmp from the pairwise line it will negotiate a connection ?!?! :confused:

---

### Post by Ayuthia on 2009-01-14
Have you tried connecting with WPA manually?  Here is a link that might help:
[http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)

I don't use Network Manager so when I need to connect with WPA, I do it manually based on the instructions in the link above.

Hopefully that will help you.

---

