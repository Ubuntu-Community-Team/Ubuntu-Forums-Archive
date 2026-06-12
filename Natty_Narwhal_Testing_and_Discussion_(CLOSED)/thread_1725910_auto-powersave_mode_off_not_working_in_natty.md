---
title: "auto-powersave mode off not working in natty?"
date: 2011-04-10
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by MAFoElffen on 2011-04-10
Ubuntu Server 11.04beta1, 32bit.

Okay... I had this worked out in previous releases, but now?  

Used to be that if you typed in ```
setterm -powersave off
```then by 10.10, I had to change that by appending ```
apm=no
(" noapm " also worked)
```to the kernel boot line in Grub2 to get it to take affect... Now, none of those seem to turn the apm off.  That in itself is strange and curious in itself, as that should be the linux kernel standard. with regards to kernel boot options, right?

Okay, now what?  I know that when I boot into tty text console mode with the attached monitor and keyboard that it's using tty1... At least, that's what it says as it's starting that session. but ```
-$ dmesg | grep tty
[    0.000000] console [tty0]  enabled
[    0.238651] serial250: ttyS0 at I/O 0x3f8 (irq = 4) is a 1650A
[    0.324953] serial250: ttyS1 at I/O 0x2f8 (irq = 3) is a 1650A
[    0.366663] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 1650A
[    0.452837] 00:0a: ttyS1 at I/O ox2f8 (irq = 3) is a 1650A

```So... Any ideas on what to try now in Natty to get this to work?

---

