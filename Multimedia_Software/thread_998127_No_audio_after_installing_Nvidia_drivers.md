---
title: "No audio after installing Nvidia drivers"
date: 2008-11-30
forum: Multimedia Software
---

### Post by LolitaRainking on 2008-11-30
Why does the audio (via Soundblaster Audigy LS) stop working after installing Nvidia restricted drivers? It starts working as soon as I disable the drivers. I've tried with 173.x, 177.x and 180.x series. It's driving me mad. I can choose between audio or resolution over 800x600. I want both!

Running Intrepid Ibex with an Nforce 630i-/Geforce 7100-based motherboard.

---

### Post by markbuntu on 2008-11-30
I have heard of this problem and it seems to be because they are both trying to use the same fixed pci interrupt. I think it is number 10 or 12. Look in your syslog.

---

### Post by LolitaRainking on 2008-12-01
So how do I go about to change one of them and to what?

---

### Post by Grumpster on 2009-05-24
Don't you love it when they tell you what the problem is and don't tell you how to fix it. I've got the same problem and need the same answer.

---

### Post by xc3RnbFO8P on 2009-05-24
Maybe something like this (in Bios):
> Manually change the interrupt assigment for Slot 4/5 in the system's bios
setup:
"Advanced" -> "PCI Configuration" -> "Slot 4/5 IRQ": change from AUTO to IRQ10

---

