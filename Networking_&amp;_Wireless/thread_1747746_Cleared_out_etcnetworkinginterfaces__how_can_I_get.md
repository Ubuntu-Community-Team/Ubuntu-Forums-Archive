---
title: "Cleared out /etc/networking/interfaces : how can I get it back?"
date: 2011-05-03
forum: Networking &amp; Wireless
---

### Post by FerretWithASpork on 2011-05-03
So I accidentally deleted everything in my /etc/networking/interfaces files....... is there any way to make a new one?

---

### Post by chili555 on 2011-05-03
Sure. Here ya go:```
sudo gedit /etc/network/interfaces
```Add two lines:```
auto lo
iface lo inet loopback
```Proofread, save and close. In the future, for safety's sake, make a backup before you experiment:```
sudo cp /etc/somefile /etc/somefile.bak
```You can always restore the backup. ```
sudo cp /etc/somefile.bak /etc/somefile
```I think you could do it the GUI way with gedit; do a 'Save As' and add .bak to the name. Reopen the file so you are making your changes to the original, not the bak.

---

### Post by FerretWithASpork on 2011-05-03
Wifi works again :D Thanks a bunch!

---

