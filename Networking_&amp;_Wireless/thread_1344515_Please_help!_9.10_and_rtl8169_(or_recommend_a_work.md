---
title: "Please help! 9.10 and rtl8169 (or recommend a working gigabit pci card)"
date: 2009-12-03
forum: Networking &amp; Wireless
---

### Post by maxxerific on 2009-12-03
hello all, 
   i've spent the entire day trying to get my rtl8169 gigabit pci card working and i'm getting really really upset ;)

i tried using the rtl8168 drivers no luck
i can't compile a the drivers form  the realtex websight.
the default drivers sjipped with 9.10 won't let the crad detect a link 

does anyone have this working under 9.10? 

if not - can anyone recommend a giganit NIC that is working flawlessly out of the box?

---

### Post by maxxerific on 2009-12-04
haha 

"giganit"

---

### Post by matt06 on 2009-12-04
The only thing I can tell you is that mine is still working as an upgrade from 9.04 to 9.10.

---

### Post by maxxerific on 2009-12-04
hey matt
  are you using the drivers which ship with ubuntu - or did you compile from realtek's website?

---

### Post by matt06 on 2009-12-04
IIRC, I just threw it in my 9.04 box and it worked, but I could be mistaken.  Here is my dmesg for reference.

```
matt@mythtv:~$ dmesg | grep 8169
[    1.667893] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.667921] r8169 0000:02:07.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.667961] r8169 0000:02:07.0: no PCI Express capability
[    1.731683] eth0: RTL8169sb/8110sb at 0xdf8a0000, 00:14:d1:xx:xx:xx, XID 10000000 IRQ 23
[   15.753487] r8169: eth1: link up

```

and some more info to hopefully help you:

```
matt@mythtv:~$ lsmod | grep 8169
r8169                  32064  0
mii                     5212  1 r8169
matt@mythtv:~$ locate r8169.ko
/lib/modules/2.6.28-16-generic/kernel/drivers/net/r8169.ko
/lib/modules/2.6.31-15-generic/kernel/drivers/net/r8169.ko

```

---

