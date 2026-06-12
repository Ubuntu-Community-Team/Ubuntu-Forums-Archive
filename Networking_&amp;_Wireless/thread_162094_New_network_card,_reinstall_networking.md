---
title: "New network card, reinstall networking?"
date: 2006-04-18
forum: Networking &amp; Wireless
---

### Post by Elrohir on 2006-04-18
Hi! REcently bought a new network interface card... D-Link DFE-530TX... before placing it on a PCI slot, do I need to reinstall networking? how do I do this? if not, does Ubuntu recognize it on boot-time?

Thanx in advance...

---

### Post by tkiesel on 2006-04-18
If you're pulling out the old card and replacing it with the new one, you shouldn't have to worry about a thing. Everything will auto-detect, and all of our settings specific to the old network card should carry over!

Happened to me when I had to replace a Netgear card that was dying. (At the time I dual-booted with Ubuntu and Windows XP. Interestingly enough, the card was breaking in such a way that it worked perfectly in Ubuntu but was dead in Windows.)

You should be good to go! :)
-T

---

### Post by localzuk on 2006-04-18
IIRC, it should 'just work'. You should be able to open the Networking application and configure it straight away.

---

### Post by Elrohir on 2006-04-18
that in case I'm replacing an old one... but no, thats not the case... I bought this new one to share internet with a second PC...

---

### Post by localzuk on 2006-04-18
If you stick a new card in, it will be recognised on start up and added to the networking control panel application where you will be able to edit it straight away... There is no need to do any re-installing. :)

---

### Post by Elrohir on 2006-04-18
that was the answer I was looking for... I hope it works... I'll reboot and tell you guys what happened...

---

### Post by Elrohir on 2006-04-18
ok, new problem...

So now I have 2 network interfaces, internet and local network...

local network (lets call this one server) has a static IP address (192.168.0.1) and the other PC (lets call it Nessa) has 192.168.0.2

so in Nessa I ping the Server but there is no reply... on the Server, I have activated Firestarter... Firestarter is already configured to share internet with Nessa... In server, I ping Nessa and the same, no reply...

any ideas?

---

### Post by Elrohir on 2006-04-18
quick question... how do I reinstall networking... Nessa's old NIC didnt work, so I replaced it with a new Encore ENL832-TX NIC, but it seems that Nessa doesnt recognize the NIC... I run ```
lspci
```and it is listed, but when I go to System > Administration > Networking, no NIC is listed...

---

### Post by Elrohir on 2006-04-18
this is what I get when I run "lspci -mv":
```
Device:    01:0a.0
Class:    ffff
Vendor:    Realtek Semiconductor Co., Ltd.
Device:    8131
Rev:    ff
ProgIf:    ff
```

---

