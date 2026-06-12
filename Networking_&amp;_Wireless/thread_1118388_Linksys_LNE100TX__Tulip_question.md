---
title: "Linksys LNE100TX / Tulip question"
date: 2009-04-06
forum: Networking &amp; Wireless
---

### Post by Rofii on 2009-04-06
I've tried installing a new LNE100TX NIC only to have it not recognized, so I did a search through apt for this tulip thing I keep hearing about and installed nictools-pci. From there I found the tulip-diag command and did that. I receive the following output and am unsure where to proceed from here:

```
tulip-diag.c:v2.18 11/12/2003 Donald Becker (becker@scyld.com)
 http://www.scyld.com/diag/index.html
Unable to find a recognized card in /proc/pci.
If there is a card in the machine, explicitly set the I/O port address
  using '-p <ioaddr> -t <chip_type_index>'
 Use '-t -1' to see the valid chip types.
```

I'm unsure where to find the I/O address and I'm not quite sure what they mean by chip type index. Would anyone be so kind as to point a noob in the right direction? ;)

---

### Post by kreggz on 2009-04-06
try:
```
lspci -v 
```

that should tell you all the information about the card

Is this an old PC??

---

### Post by Rofii on 2009-04-07
No it's less than a year old. Intel E8400, 3072MB ram, GeForce 9800.

I'll try that command ASAP, I need to do a reinstall first. I'll post once I try it out.

---

