---
title: "Erros setting fs.file-max in sysctl.conf"
date: 2009-07-20
forum: Networking &amp; Wireless
---

### Post by reezer on 2009-07-20
Hey guys,
I'm trying to increase the maximum number of connections. I edited posix_types.h and typesizes.h fine.

But when I run "sysctl -w fs.file-max=131072"  I get "*error: "Operation not permitted" setting key "fs.file-max" *"

Any help would be greatly appreciated.

---

