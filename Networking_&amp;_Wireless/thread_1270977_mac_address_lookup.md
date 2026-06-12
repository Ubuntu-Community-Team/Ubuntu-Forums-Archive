---
title: "mac address lookup"
date: 2009-09-20
forum: Networking &amp; Wireless
---

### Post by flylehe on 2009-09-20
Hi,
I just read some introductory tutorial about Mac address. It seems that a wireless card in a computer has a unique Mac address (representing the manufacture and serial number of the network adapter). So does it mean that given a Mac address, it is possible to identify which computer worldwide is using the corresponding wireless card? If yes, how is it to be done basically?
Thanks and regards!

---

### Post by kidders on 2009-09-21
Hi there,

> **flylehe said:**
> It seems that a wireless card in a computer has a unique Mac addressIn theory, that's true. In practice, MAC addresses are sometimes re-used by certain manufacturers, and many devices support address spoofing. As a result, assuming you even have *access* to the MAC layer in the first place (ie you're on the same subnet as the adapter you're interested in, and there's no routing going on between it and you), MAC addresses are of limited enough practical use.

> **flylehe said:**
> So does it mean that given a Mac address, it is possible to identify which computer worldwide is using the corresponding wireless card?MAC addresses are tied to network adapters, not computers ... There's no way to tell what computer is using a card you're interested in.

What are you thinking of trying to do?

---

### Post by flylehe on 2009-09-21
Please correct me if I am wrong. I think airodump-ng gives the Mac addresses of those network adapters that are connecting to my wireless. So if there is any of them that is different from ourselves, is it possible to identify where it is and whom it belongs to?

---

### Post by kidders on 2009-09-22
Ah, I see ...

No, that's not possible. In theory, since the manufacturers of many computers with built-in wireless cards ask end users to register their purchases, you *might* be able to identify the owner of a given MAC address, of you had access to that company's customer database. You'd be assuming, of course, that your "visitor" didn't change his MAC address before trespassing on your network ... which is highly likely.

---

### Post by cbugsubunt on 2009-09-22
there is a **mac database** on the net.you can search at least the manufacture if that is a good start for you. (*if they didnt mask there MACadd )wich am shure they did.:-k

---

