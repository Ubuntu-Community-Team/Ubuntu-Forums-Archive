---
title: "Wireless Chipset Dead"
date: 2010-06-21
forum: Networking &amp; Wireless
---

### Post by artcarney on 2010-06-21
Hi all.

It looks like my laptop's wireless chipset (Broadcom) has/is dying. It won't work anymore on my Lucid install whereas it was working perfectly. The warrenty is long expired.

lspci brings up nothing about it anymore, it once did.

I booted my laptop into Win7 and it no longer finds it either. The manual slider switch on my HP Pavillion dv6000 is in the on position but the light is yellow.

It will very rarely work on Win7 now.

I can't afford a new laptop just now so it looks like I need an external wireless adaptor. I have (open busses) USB, cardbus/54, and a small firewire port. It does not pcmcia or other busses.

Suggestions for an external adaptor that plays nicely with Lucid would be appreciated as any other valid suggestions.

Any particular chipsets to look for or avoid?

---

### Post by Joe of loath on 2010-06-21
Chances are the internal one is a mini-pci card. They're easy enough to replace, and cheap enough on ebay. I assume it was a BCM43XX? IIRC the 'dell 1397' wifi card (BCM4312) is about £15 on ebay. I'm not saying it plays nicely, but it's cheap and should use the same drivers as your current one.

---

### Post by artcarney on 2010-06-22
> **Joe of loath said:**
> Chances are the internal one is a mini-pci card. They're easy enough to replace, and cheap enough on ebay. I assume it was a BCM43XX? IIRC the 'dell 1397' wifi card (BCM4312) is about £15 on ebay. I'm not saying it plays nicely, but it's cheap and should use the same drivers as your current one.

Not too sure I want to disassemble my laptop, I need it too much.

Can spend about the same money for a USB wireless network card, just want to know what chipsets are easily recognized by Ubuntu hopefully with no/few extra packages needing to be installed.

---

### Post by Joe of loath on 2010-06-22
There's no disassembly involved, just removing an inspection panel on the bottom. My dell even has instructions in the manual it comes with on how to do it, so it's meant for your average user to be able to replace.

---

### Post by artcarney on 2010-06-23
> **Joe of loath said:**
> There's no disassembly involved, just removing an inspection panel on the bottom. My dell even has instructions in the manual it comes with on how to do it, so it's meant for your average user to be able to replace.

I took a look and two screws, two wires and unplug it, then plug in the replacement and reverse the disassembly and it's a done deal.

The new (to me) replacement network card is on order.

Until then, my Nexus One has Froyo installed (Google's latest Android OS based on Linux) and it allows either wifi or USB tethering. I'm using the latter.

See results:

[http://www.dslreports.com/im/89961352/1061.png](http://www.dslreports.com/im/89961352/1061.png)

---

