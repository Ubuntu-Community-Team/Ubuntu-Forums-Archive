---
title: "WiFi Works after suspend, but not startup"
date: 2009-08-05
forum: Networking &amp; Wireless
---

### Post by Trind on 2009-08-05
I have an Acer Aspire One ZG5 with an Atheros AR242x wireless card and I have had problems with wireless ever since I installed Ubuntu Netbook Remix and everytime I update. The topics on this board have been very helpful so far but I can't find the solution to this problem.

The latest problem I've had is that wireless does not work upon startup. I have to put the netbook into suspend, and then wake it back up for wireless to work. What do I need to do to configure the netbook to start wifi upon startup?

Thanks.

---

### Post by MadHatter21 on 2009-08-05
What driver did you install on your system? Have you put the driver in the /etc/modules file? You dont have to use netbook remix, i have my netbook running desktop version with an atheros card running ath9k (The Driver that your card uses) and it works fine now after a little bit of troubleshooting. I can help you install ath9k on desktop if you want, but i think there might be a problem with it on net remix.

MadHatter21

---

### Post by Trind on 2009-08-05
My wifi driver is madwifi. In Hardware Drivers it says that it is not activated and when I activate the driver it says that it is disabled but still in use.

How do I check to see that I have the driver in etc/modules/ folder? What file am I looking for?

---

### Post by Trind on 2009-08-07
Bump

---

