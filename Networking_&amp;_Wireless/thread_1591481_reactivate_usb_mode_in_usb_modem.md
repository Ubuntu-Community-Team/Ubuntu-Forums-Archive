---
title: "reactivate usb mode in usb modem"
date: 2010-10-09
forum: Networking &amp; Wireless
---

### Post by Tedel on 2010-10-09
hi there,

Long ago, I used the information on this page...

wiki.archlinux.org/index.php/ZTE_MF626_/_MF636

...to be able to configure the usb modem in my linux computer. As I've been using Linux there onwards, I didn't mind any longer.

Now I plugged the usb into a windows computer but the driver installation routine doesn't start. It's obvious that's because I deactivated the cd mode. How do I bring it back?

---

### Post by e79 on 2010-10-09
Is your USB modem/dongle detected by your Windows ? If so, can you go to 'My Computer' and see if a drive letter (ie  E: )  as been assigned to this device ? If so, can you 'enter' the device and see if you have any executable files you could launch ?

---

### Post by alexfish on 2010-10-09
Hi

for ZTE devices only

AT commands

dissable CD
AT+ZCDRUN=8

enable CD
AT+ZCDRUN=9

alexfish

---

