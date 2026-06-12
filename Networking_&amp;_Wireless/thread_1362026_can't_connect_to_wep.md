---
title: "can't connect to wep"
date: 2009-12-22
forum: Networking &amp; Wireless
---

### Post by voteforcondit on 2009-12-22
i am running unbuntu 
i can connect to any unlocked wireless network fine
cannot connect to a wep at my girlfriends
 i know i have the right pass key and such. 
i have checked and rechecked it with her windows comp
but no luck on mine. 

i have a bcm4206 802.11b/g wireless lan controller

---

### Post by ajgreeny on 2009-12-22
There are two or three options for entering passphrase/key for the different wep encryption types, so make sure you are using the right one.  If you enter the key, it has to be the encrypted version, if I remember correctly, not the passphrase/password itself.

I had exactly your problem the first time I used wep security mode on a laptop with a netgear WG511v2 with a marvel chip.  Using ndiswrapper I can get it to work, but not with WPA, only wep, and that's how I found out about this differing entry type for wep encryption.

---

### Post by voteforcondit on 2009-12-22
yeah i get that and i have the right key and i feel im entering it right

maybe a way to do it through command line?

---

