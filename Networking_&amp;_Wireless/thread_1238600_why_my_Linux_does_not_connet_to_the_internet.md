---
title: "why my Linux does not connet to the internet?"
date: 2009-08-12
forum: Networking &amp; Wireless
---

### Post by ieBrazil on 2009-08-12
Why does it happen?

I have a dual boot on my laptop. The windows connection works just fine, you see. But when I use the Ubuntu 9.04, it hardly ever works...  

Why? What do I need to do in order to resolve it?

tnx!

---

### Post by Iowan on 2009-08-12
> **ieBrazil said:**
>  it hardly ever works... But it does, sometimes? Post results of **ifconfig -a** and **lshw -C network**
 Are you trying wired, wireless, or both?

---

### Post by ieBrazil on 2009-08-12
> **Iowan said:**
> But it does, sometimes? Post results of **ifconfig -a** and **lshw -C network**
 Are you trying wired, wireless, or both?

Just trying wireless.

How do I get those results, though?

---

### Post by Iowan on 2009-08-12
Open a terminal (Applications>Accessories>Terminal) and enter the commands.  If the machine is connected to Internet, you can copy/paste results... otherwise, you can append "> filename" to copy the results to a file named "filename" (eg. **ifconfig -a > ifconfig.txt** to save results to file named "ifconfig.txt"). You can copy that to a transportable media (USB drive, floppy, etc.) to be used on a machine with Internet access.

There are probably easier/better ways...

---

