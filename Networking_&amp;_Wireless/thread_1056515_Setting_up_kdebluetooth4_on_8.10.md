---
title: "Setting up kdebluetooth4 on 8.10"
date: 2009-01-31
forum: Networking &amp; Wireless
---

### Post by mpl34 on 2009-01-31
Hey,

I own a dell vostro with recently installed kubuntu 8.10 at first i did not mind using the touch-pad however, lately it has really started to frustrate me. From other posts i have read it seems to be a problem with kde4. I have read that installing bluez is required but am very new to this and don't want to just install everything i see.

some advice would be much appreciated

---

### Post by mpl34 on 2009-02-01
After abit of research i found the following 

sudo apt-get install bluez-compat
sudo hidd --search

Which found my bluetooth mouse and connected it automatically however kdebluetooth still does nothing when i click on it i would have thought that a bluetooth icon would appear in the task tray. Also i have to search for my bluetooth devices after every reboot.

---

### Post by mpl34 on 2009-02-01
After more research i added

HIDD_ENABLED=1
HIDD_OPTIONS="-i 00:12:5A:69:3B:46 --server"

to /etc/default/bluetooth, note no /etc/default/bluez-utils exists but i assume they are equivalent. However this has seemed to have no effect i'm stilling having to manually connect each time i reboot.

---

