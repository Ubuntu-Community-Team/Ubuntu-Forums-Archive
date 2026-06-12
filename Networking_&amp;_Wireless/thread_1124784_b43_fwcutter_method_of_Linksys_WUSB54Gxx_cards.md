---
title: "b43 fwcutter method of Linksys WUSB54Gxx cards"
date: 2009-04-13
forum: Networking &amp; Wireless
---

### Post by Necrom@ncer on 2009-04-13
I have heard of this, but don't know how to use it, can i be enlightened?

---

### Post by RedSingularity on 2009-04-13
b43 fwcutter is in the repositories if you want to download it.  It can be found in package manager.

---

### Post by Necrom@ncer on 2009-04-14
Thanks, but that really doesn't help me, I have a wireless card WUSB54gsc with broadcom chipset and was pointed to b43 fwcutter, I installed it via apt-get, had it fetch the firmware, but i don't have a clue what to do next.

---

### Post by RedSingularity on 2009-04-14
Post the output of "lspci" in the terminal.

---

### Post by Necrom@ncer on 2009-04-14
Nevermind, I got a WPC54G for 12.48 at target, worked with ndiswrapper,

---

### Post by RedSingularity on 2009-04-14
Nice......that a PCI or USB??

---

### Post by Necrom@ncer on 2009-04-15
pcmcia, target's getting rid of wireless g PCI/PCMCIA cards to make room for wireless Ns. get 'em while they last, if you're interested, it works with win98 as well, but copy the 9x folder to your HDD and point ndis gtk to it

---

