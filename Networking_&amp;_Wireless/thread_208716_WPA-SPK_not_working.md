---
title: "WPA-SPK not working"
date: 2006-07-04
forum: Networking &amp; Wireless
---

### Post by Trab on 2006-07-04
i know this is a common problem, but im hoping ive just over looked something, and it works fully.
i currently have 2 APs in my network, one that has no encryption (a different computer on my network cannot connect otherwise) and one that has wpa-spk on it.
im trying to use the gnome-network-manager with it.
the device is a netgear wg311t card, and should work fine.
the issue is when i go to put in the key, it ask for wpa-personal (which i believe is the same as psk) but the key is already in hex. so do i need to convert the key i have out of hex so it isnt double hexed?
thanks
-Trab

---

### Post by Agent86 on 2006-07-04
Network Manager wants the passphrase, not the hex key. So yes, you need to convert it from hex back to the passphrase form.

---

### Post by Trab on 2006-07-04
kk how can i do that?

---

