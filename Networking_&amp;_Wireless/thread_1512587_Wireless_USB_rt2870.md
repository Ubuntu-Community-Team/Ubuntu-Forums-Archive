---
title: "Wireless USB rt2870"
date: 2010-06-18
forum: Networking &amp; Wireless
---

### Post by Hogeyfur on 2010-06-18
I'm looking to upgrade to lucid so far i've set up a virtual machine to test it and mainly to try and get my wireless adapter working. 

So far its been a partial success. My adapter shows up but now it just loops between asking for my password and the connection phase 

These are the steps i took so far 

```

sudo nano /etc/modprobe.d/blacklist.conf 

**In blacklist.conf**
blacklist rt2800usb
blacklist rt2x00usb
blacklist rt2x00lib

**After saving my changes **
sudo su 
echo rt2870sta >> etc/modules

```I then rebooted and thats where i've got now. No idea what to do next

---

