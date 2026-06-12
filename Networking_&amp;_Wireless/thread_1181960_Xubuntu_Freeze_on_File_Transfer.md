---
title: "Xubuntu Freeze on File Transfer"
date: 2009-06-08
forum: Networking &amp; Wireless
---

### Post by muskatnuss on 2009-06-08
hi guys

so my problem: 

i got an fresh xubuntu install -> added nfs client / server, samba client / server and shared an partition i have mounted in /media/partition with it. everytime i start copying one or more files the server freezes... eg i use it as client!!! file moving on local disk is no problem! 

what could be the problem...

//edit also tried to copy an file from my home partition -> same problem occurs

//2edit now i tried to copy over scp -> result: FREEZE

//3edit now i tried to download an file via web browser 900 Mb -> no Problem
but copying over web browser from local network causes the machine to freeze!!!

---

### Post by muskatnuss on 2009-06-09
bump -> nobody knows what to do ?

i have now done an bios update -> and resetted everything to its default.
still no result my computer hangs on network traffic only!

---

### Post by dmizer on 2009-06-19
Are you sharing the file with samba or nfs? Are you mounting the share with samba or nfs?

Do you have a need for both samba and nfs? It would be better to use one or the other rather than both.

---

