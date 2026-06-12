---
title: "compiling wireless driver for a kernel with l7 patch"
date: 2009-08-11
forum: Networking &amp; Wireless
---

### Post by janascii on 2009-08-11
I'm running a server with layer7 running on the kernel(ebox) and need to compile a wireless driver.  **uname -r** returns a name with l7filter on the end so whenever the make file looks for the linux-headers-..., it kicks out of the compiler.  Any suggestions?

running:
8.04 server(ebox 1.2)
ralink 2860 card

---

