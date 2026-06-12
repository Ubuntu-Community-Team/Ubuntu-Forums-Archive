---
title: "My wireless card on Ubuntu 9.04?"
date: 2009-04-23
forum: Networking &amp; Wireless
---

### Post by qjmoss on 2009-04-23
With 8.10 there was steps in the release forum to get my wireless card working. I'm running my laptop with a AR242x 802.11abg Wireless PCI Express Adapter. I was wondering if 9.04 is compatible with this wireless card.


Thank you for your time :)

---

### Post by SuperSonic4 on 2009-04-23
Jaunty uses the (free) ath5k driver for atheros cards now - mine was recognised out of the box in kubuntu jaunty (beta)

```
04:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
``` is the model I'm using

---

### Post by qjmoss on 2009-04-23
Well, I'm taking a chance updaiting, I don't have a USB drive so I can't do a boot live. I'm a little nervous.  What do you think? do it or no ; )

---

### Post by SuperSonic4 on 2009-04-23
If you've backed up your data then go for it :p
If not, back up and go for it xD

It's up to you, if intrepid works then there is no logical reason to change but then I like being near the cutting edge :p

---

### Post by qjmoss on 2009-04-23
I have a 1tb external hard drive.  How would I back everything up, and get it working again 


Sorry if this is a veryy noob question, I've just never went about this, and I've always wanted to know =)!

---

### Post by SuperSonic4 on 2009-04-24
It depends what you want back up. If you wanted to back up your home directory and all it's contents (app settings and personal documents not stored elsewhere) you could use cp. Something like ```
cp -Rv ~ /media/disk
```

---

### Post by t0mppa on 2009-04-24
```
06:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
``` Here as well, I had MadWifi (not ath5k) drivers set up on 8.10 and the upgrade didn't kill them or anything, they're still rolling and didn't have to touch a thing concerning wireless. Did run into some other trouble, so a back up is always a good idea.

---

