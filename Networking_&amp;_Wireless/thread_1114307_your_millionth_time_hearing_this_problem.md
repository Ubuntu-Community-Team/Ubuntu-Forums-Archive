---
title: "your millionth time hearing this problem"
date: 2009-04-02
forum: Networking &amp; Wireless
---

### Post by His on 2009-04-02
Here is your millionth time hearing this problem...

The problem: My wireless card doesn't work. 

The system: Acer Aspire 5720-4126. The wireless NIC is an Acer InviLink 802.11b/g ... you may also call it an Atheros AR5BXB63.

I'm running: The Ibex 8.10.

I've tried: I think I've tried everything that I've seen on ubuntuforums and google that relates to this card.

Any tips?

---

### Post by cariboo on 2009-04-02
I would suggest you install the backport-modules, as they have a newer driver for your wifi device. I believe they are called the ubuntu-backports or Intrepid-backports. I'm not on a system running Ubuntu at the moment, so I can't look in the repositories.

Jim

---

### Post by His on 2009-04-03
Well, earlier in my poking around I must have fixed it. I just switched to linux to try what you suggested and vioala! it worked after I modprobe'd ath_pci. I had already installed madwifi... and restarted... so I don't know what I did to fix it...

Thanks though.

---

