---
title: "Boot without network support (on the fly)"
date: 2006-01-04
forum: Networking &amp; Wireless
---

### Post by TECsBrain on 2006-01-04
Is there a way I can add an entry to GRUB that will allow me to boot Ubuntu without network support (to solve that hang from "Configuring network devices" or whatever it is) when I do not need network support?  Something like a -nonet flag I can staple onto the boot string?  When I am not near a wireless hotspot my computer can identify, I experience a similar problem to other laptop users where "Configuring network devices" hangs for a long amount of time.

---

### Post by oakz on 2006-01-04
not sure about the boot menu option, but if you enter ctrl-c while the net devices are hanging the init process continues

---

### Post by ape on 2006-01-04
You can also install the ifplugd package.

---

### Post by TECsBrain on 2006-01-04
I've got wifi going at times; I'd better stick with ctrl-c

Thanks for your help.

---

