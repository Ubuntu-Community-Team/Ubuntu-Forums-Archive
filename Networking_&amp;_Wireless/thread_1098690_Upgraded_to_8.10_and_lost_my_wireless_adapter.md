---
title: "Upgraded to 8.10 and lost my wireless adapter"
date: 2009-03-17
forum: Networking &amp; Wireless
---

### Post by The Neurochild on 2009-03-17
Hi

I recently upgraded my Ubuntu from Hardy Heron (8.04) to Intrepid Ibex (8.10) and after doing the process with the alternate CD installation, I later found myself without my wireless connection. I have a Compaq Presario 2500 laptop with a Broadcom BCM4311 internal wireless adapter working with b43-fwcutter in Hardy.

Do I have to re-download the b43-fwcutter (as it was updated to a new version)? Or is there another way to get the adapter work again? I heard Broadcom launched a new driver to the BGM4311 for Linux systems, but I don't want to mess with codes right now.

Greetings...

The Neurochild

---

### Post by D3ath on 2009-03-17
Seems like you need to mess with "codes" to get it to work.  That or go back to 8.04?  April will release the 9.04 so maybe you could wait till then.  I'm sure it will get clear up by then.  All depends on how bad you want it to work...

---

### Post by The Neurochild on 2009-03-17
Very badly!

---

### Post by D3ath on 2009-03-17
Do you have the package still installed or did you remove the package? If it is installed try running:

```
sudo dpkg-reconfigure b43-fwcutter
```

In Synaptic Package Manager this driver should be there. If you do not have it installed try installing it again. Let me know what happens.  O yea make sure you connect via ethernet during all this.

---

### Post by The Neurochild on 2009-03-17
I'll give a try tonight. Thanks!

---

