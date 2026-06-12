---
title: "wireless not working after installing vmware"
date: 2009-04-05
forum: Networking &amp; Wireless
---

### Post by dubesinhower on 2009-04-05
i recently installed ubuntu on my compaq presario cq69 215dx. it has an atheros ar242x wireless card in it. ive installed the madwifi drivers using these directions. [http://madberry.org/2008/11/how-to-get-atheros-ar242x-to-work-on-810-intrepid-ibex/]("http://madberry.org/2008/11/how-to-get-atheros-ar242x-to-work-on-810-intrepid-ibex/"). wireless worked after installing these drivers. then yesterday, i installed vmware, and today my wireless doesnt work. earlier today, when i clicked the network connections icon in the system tray, it only had wired as an option. so i just now reinstalled the madwifi drivers. wireless shows up on the list now, but i still cannot connect to my network. any help?

also, i created a wireless network by accident. how can i delete or remove it?

---

### Post by dubesinhower on 2009-04-06
bump because this is making me mad. anyone have ideas?

---

### Post by superprash2003 on 2009-04-06
type **sudo ifdown vmware0** at the terminal. where vmware0 is the vmware interface and then try wireless.

---

