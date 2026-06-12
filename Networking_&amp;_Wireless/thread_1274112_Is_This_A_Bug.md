---
title: "Is This A Bug?"
date: 2009-09-24
forum: Networking &amp; Wireless
---

### Post by joeyknuccione on 2009-09-24
My 

NetworkManager Applet 0.7.0.100

Has the X on it, and it says "No valid active connections found!", even though here I am sending this to the entirewebs.

My network has been real weird with this card, an older 3com brand, so I post this out of curiosity more than anything else.

Could this issue be related to my random network connectability?

---

### Post by bruno9779 on 2009-09-24
please post the exact model and brand of the card.
You may have to install some dependencies or NDSwrapper, but without knowing which card it is, there isn't much that can be done

---

### Post by joeyknuccione on 2009-09-24
lspci says:

Ethernet controller: 3Com Corporation 3c900 10Mbps Combo [Boomerang]

Also, now I have the X, but my "Connection Information" is available, where last night it wasn't.

I'm using the 3c59x module, if that means anything.

Does ndiswrapper work for ethernet cards? I thought that was for wireless.

---

### Post by Iowan on 2009-09-24
Check contents of */etc/network/interfaces* - it *should* have only tow lines configuring "lo". If there is a definition for your network card (probably eth0), then NM won't (or isn't supposed to) touch it... and claims "no connections".

---

