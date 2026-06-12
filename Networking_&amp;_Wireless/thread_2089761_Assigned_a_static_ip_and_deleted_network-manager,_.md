---
title: "Assigned a static ip and deleted network-manager, eth0 not starting on boot"
date: 2012-11-30
forum: Networking &amp; Wireless
---

### Post by mushy365 on 2012-11-30
Now i have a slight problem, When i reboot i always have to issue an ifup eth0 to make it have any network connectivity. 
 
This isnt ideal as im going to turn it into a server and will only be accessing it remotely, i can't do that if it boots with eth0 turned off. 
 
Is there a problem or do i have to do something to make this happen automaticaly?

---

### Post by steeldriver on 2012-11-30
If you're defining the interface via /etc/network/interfaces then you need to mark it as 'auto' I think

```
# The primary network interface
**auto eth0**
iface eth0 inet static
.
.
.

```

---

### Post by mushy365 on 2012-11-30
Ok, will give it a try when i get home from work! Hopefully that sorts it.

---

