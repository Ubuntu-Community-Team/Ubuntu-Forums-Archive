---
title: "Rsync from Ubuntu TO Windows"
date: 2009-07-28
forum: Networking &amp; Wireless
---

### Post by djtecha on 2009-07-28
Ok, this is killing me here. I am trying to use rsync to basically keep to HDD's the same but in different computers, still on the same network though. I can get rsync working on the Ubuntu box, just playing around, but when I try to have it interact with Windows it just hangs there. My command from the Ubuntu box is:
sudo rsync -rtvu --modify-window=1 --progress --delete --exclude-from=/home/dante/excludeList.txt /media/storage/*.pdf djtecha@192.168.1.116:C:

which I though hey maybe the location is wrong, but then it would usually tell me something along the line of "location does not exist." And everywhere I look there are ways to get rsync to go from Windows To Ubuntu but can't I go the other way? Please help someone.

 ~Dan

---

### Post by djtecha on 2009-07-29
Anyone have any recomendations?

---

