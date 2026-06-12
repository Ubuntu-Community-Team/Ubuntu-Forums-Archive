---
title: "Computer name"
date: 2009-11-24
forum: Networking &amp; Wireless
---

### Post by rolandpish on 2009-11-24
Hi all.
I recently installed Karmic Koala.
Which packages do I need to install in order to let other computers on the network make a ping on my pc using my computer name?

Thanks in advance

---

### Post by Iowan on 2009-11-24
Depending on how the network is set up (DHCP server in particular), you will probably need to edit */etc/dhcp3/dhclient.conf*. Change the line:```
send host-name "<hostname>";
``` to use your hostname in the quotes.
BTW, to edit the file, you may need to use either```
sudo nano /etc/dhcp3/dhclient.conf
``` or ```
gksudo gedit /etc/dhcp3/dhclient.conf
```

---

