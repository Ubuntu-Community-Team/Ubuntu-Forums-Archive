---
title: "trouble install NIC"
date: 2009-07-01
forum: Networking &amp; Wireless
---

### Post by Arrick on 2009-07-01
I am trying to install a second network card (a trendnet TEG-PCITXR HW/2.1).  With the card in, the computer refuses to boot, and no text appears on the primary terminal.  With the card removed, the computer boots fine.

The computer is an HP Proliant ML110, and the original network connection is integrated to the motherboard.

Is there anything anyone can suggest to try, before I assume the network card is bad?

Thanks,

Al

---

### Post by buzzmandt on 2009-07-01
does the bios post at least?

---

### Post by Arrick on 2009-07-02
> **buzzmandt said:**
> does the bios post at least?
Well, at first it didn't, which should have been an indication that this was the wrong forum to post a problem.  I might have figured that out if I hadn't been fighting with hardware for the last few hours, and could think straight.

After disabling PXE from the BIOS, (no clue why this worked...)it comes up and shows the second card as eth1, and inactive, both from ifconfig and the   Administration Network Tools.  As long as I'm here, how do I get it active and recognized?

This particular box lives at a fixed IP on our company LAN.  My intention is to use the second interface to test some internet device connections.  Right now, I'd like to check DHCP functionality without involving the whole company network.  I'd like to have my box serve as a DHCP server for a 10.10.x.x network on the second card, while it continues at it's fixed ip on the 192.168.x.x network on the first card.

Am I dreaming?

---

