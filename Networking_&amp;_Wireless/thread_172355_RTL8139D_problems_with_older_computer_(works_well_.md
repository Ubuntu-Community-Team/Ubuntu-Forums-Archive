---
title: "RTL8139D problems with older computer (works well in new computer)"
date: 2006-05-08
forum: Networking &amp; Wireless
---

### Post by FSO on 2006-05-08
I just bought a cheap RTL8139D chipset based NIC, and I put it to 400 mhz pentium running Breezy. It was not detected, even lspci didn't say anything. I tried it on other Breezy-running computer, 350 mhz pentium. It was not detected, everything was like above. Then I tried it in Sempron 2800+ ( Abit KU8 ) and Athlon 64 3500+ ( Abit AV8 ), both running Breezy. NIC worked straight without any arguments. I just wonder what is the problem on that nic. I even tried older RTL8139C chipset nic, it worked in all computers, and I borrowed other RTL8139D nic, and it (un)worked like mine. I need a NIC to that 400 mhz junk, so how I can get it working?

---

### Post by mpvano on 2006-05-08
Check the bus specification for the card. Many new cards use 3.3 volt logic and assume that the PCI bus provides it. Unfortunately, there's a disagreement about whether this provision is optional or not. Many older machines simply don't provide power for newer cards.

I believe that some cards using the same chipsets provide their own power regulator to handle this problem, but others now assume the that you are using a modern PCI Bus implementation. Sometimes they list PCI 2.2 as a requirement on the box.

I have the same problem with a Netgear gigabit NIC. It won't work in some of my Pentium III era machines but will work in others, depending on the mother board model. The symptom I got was the same - no indication of the card's presence in the BIOS or in lspci in machines with no 3V power....

Fortunately, it works in the machine I need it for....

Hope this gives you one more thing to check, but it may not be your specific problem.

Mario

---

### Post by FSO on 2006-05-08
That could be the point, because I tried the NIC in a few other computers. Now I should just exchange the nic with some of my friends or so. But thanks for your help.

---

