---
title: "Issues connecting wirelessly to router."
date: 2009-11-07
forum: Networking &amp; Wireless
---

### Post by narutoko on 2009-11-07
I currently have Ubuntu 9.10 installed on my Dell Inspiron E1505 laptop. The wireless card I have on here is a Dell Wireless 1390 WLAN MiniCard. Of course, I can have a wired connection (that's how I'm communicating right now). The driver won't show up under the Hardware Drivers utility. Actually none of my drivers are being picked up. This has been a completely fresh install, just finished about 15 minutes ago. I really need HELP!!! I'm moderately new to Linux. I installed Linux as a change of pace from Windows. Any help I can get in general with this operating system will be great.

---

### Post by narutoko on 2009-11-07
I just looked at the card again on the Dell website from when I had my computer built. I clicked on the link that had the wireless card on it and it also says [SIZE=3]Dell Wireless 1490 Dual-Band WLAN MiniCard. 
[/SIZE]

---

### Post by narutoko on 2009-11-07
my situation has been resolved.

---

### Post by t0mppa on 2009-11-07
Ok, the model of the card is largely irrelevant in finding native drivers for it, it's the chip that matters. However, before I get ahead of myself, open up a terminal (Applications / Accessories / Terminal), run **lshw -C network** and post the results as that will show us the type of chip your card has and whether or not it's been associated with any drivers so far.

EDIT: You can mark the thread as solved from the thread tools.

---

