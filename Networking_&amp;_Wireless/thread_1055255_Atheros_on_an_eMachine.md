---
title: "Atheros on an eMachine"
date: 2009-01-30
forum: Networking &amp; Wireless
---

### Post by RealGeorgeW on 2009-01-30
Hello, bear with me as I'm fresh to the Ubuntu world.

I'm competent with Winblows systems and thought it'd be fun to have linux on my small laptop.

It's an eMachine D620. That's all I can tell you. I'm comfortable with the CLI so if you need me to do any commands, that's fine, but don't assume I know anything.

That said. As far as I can tell, I have an Atheros 802.11G card. It sees it, and has installed it, but for the life of me, I can't find a way to connect to a network. 

That's where I am. Drill/flame/help me, in that order if you prefer, and I'll follow along.

---

### Post by nixscripter on 2009-01-31
Atheros cards are quite notorious, but they can be made working with the right instructions.

What is the exact model of the card? Run ```
lspci -nn
``` in a Terminal to get a listing of devices.

---

### Post by RealGeorgeW on 2009-01-31
> **nixscripter said:**
> Atheros cards are quite notorious, but they can be made working with the right instructions.

What is the exact model of the card? Run ```
lspci -nn
``` in a Terminal to get a listing of devices.


Here's what it spit out :)

```

05:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter [168c:001c] (rev 01)



```

---

### Post by RealGeorgeW on 2009-02-01
Meant to put another reply.

For posterity, I'm running Ubuntu 8.10 Intrepid.

---

### Post by 5BallJuggler on 2009-02-01
Try this, different PC, but the same card.

[http://ubuntuforums.org/showthread.php?t=1054629](http://ubuntuforums.org/showthread.php?t=1054629)

---

