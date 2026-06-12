---
title: "Stuck with crummy atmel card: What can I do to make networking relatively painless?"
date: 2006-06-20
forum: Networking &amp; Wireless
---

### Post by Twinxor on 2006-06-20
I'm running el cheapo 802.11b card on my laptop, which uses the atmel wireless driver from atmelwlandriver.sourceforge.net. Ubuntu got it set up automagically, so it kind of works. But the chipset is not compatible with Network Manager (I know this firsthand!) Is there anyway to make networking a little more transparent? Ideally, I'd like to be able to go to coffeehouses and automatically connect to the free AP.

---

### Post by stupidkid on 2006-06-21
Using the command line is fine. 

iwlist <interface> scan <--- List available networks

iwconfig <interface> essid <essid_name> <--- Connects to a  network

You really dont need any gui to connect to networks.

---

### Post by Twinxor on 2006-06-21
I didn't know about that tool (iwlist) - I'll check it out.

---

