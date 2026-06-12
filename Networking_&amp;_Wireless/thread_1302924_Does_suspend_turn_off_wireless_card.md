---
title: "Does suspend turn off wireless card?"
date: 2009-10-27
forum: Networking &amp; Wireless
---

### Post by allaboutsam on 2009-10-27
Does anyone know if suspend actually turns off the wireless card (i.e., powers it down, stops it from broadcasting)? Or does it just disconnect from the network?

I am using Intrepid on a Dell Latitude D400 with a Broadcom card and the b43-pci-bridge driver.

Many thanks,
allaboutsam

---

### Post by kerry_s on 2009-10-27
yes

---

### Post by carcar1 on 2009-10-28
I think it does but I made sure it didnt cause connecting is a pain in the neck.

---

### Post by djurny on 2009-10-28
isnt the card left on to enable wakeonlan?

---

### Post by allaboutsam on 2009-10-28
Thanks, everyone.

The D400 has Wake-on-LAN, but I have it disabled in my BIOS. Assuming djurny is right, would the OS recognize that I have Wake-on-LAN disabled and thus turn off the card on suspend?

---

### Post by kerry_s on 2009-10-28
> **djurny said:**
> isnt the card left on to enable wakeonlan?

wake-on-lan is not wireless, lan is ethernet.

---

### Post by allaboutsam on 2009-10-30
Good point. Thanks again.

---

