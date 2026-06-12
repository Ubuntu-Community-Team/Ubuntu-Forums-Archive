---
title: "Wireless stopped working, disappeared from lspci"
date: 2012-12-07
forum: Networking &amp; Wireless
---

### Post by foogoo on 2012-12-07
I'm running Mint on Panp7. Wireless was working fine just 3 days ago but all of a sudden it has disappeared and doesn't appear in lspci or iwconfig. I've made no changes to the system since it was last working and I've tried turning the wireless on/off (Fn+F11) multiple times as well as restarting.

I have no idea where to even start troubleshooting what happened, does anyone have any advice? Thanks.

---

### Post by jbelmonte on 2012-12-07
Try booting from a live CD (Ubuntu) and see if wireless is working from there. If it is, then your issue is a software issue. If not, and toggling the wireless on/off switch does not help, then you may have a hardware issue. Are you still under warranty?

---

### Post by foogoo on 2012-12-07
> **jbelmonte said:**
> Try booting from a live CD (Ubuntu) and see if wireless is working from there. If it is, then your issue is a software issue. If not, and toggling the wireless on/off switch does not help, then you may have a hardware issue. Are you still under warranty?

Great suggestion, I'll try that. No definitely not, I've had it for about 2 years now. Thanks.

---

### Post by joe4ska on 2012-12-10
Does the network show up on other computers?
Perhaps the router needs a hard reboot?

---

### Post by Bucky Ball on 2012-12-10
*Thread moved to **Networking & Wireless***

---

### Post by foogoo on 2012-12-11
Well here's what I did: I booted up Mint live and same thing, no wireless, nothing in lspci or iwconfig. Frustrated I opened the bottom on the Panp7 and cleaned a bit of dust, I couldn't even find the wireless module so I closed it back up and bam, it worked. I have no idea what just happened, maybe a loose connection?

---

### Post by ahallubuntu on 2012-12-11
Internal wireless cards (mini-PCI cards) CAN come loose from their slots.  Screws that secure them can come loose, etc.  Personally, I'd find exactly where the card is (could be under the keyboard) and re-seat it.  See if there's a hardware manual online for your particular laptop.

---

### Post by Bucky Ball on 2012-12-11
Stranger things have happened ... perhaps. At least it's working.

Please mark thread as solved from 'Thread Tools' to help others. Thanks.

---

