---
title: "Shutdown Freeze with wifi on"
date: 2011-10-04
forum: Networking &amp; Wireless
---

### Post by stroduces on 2011-10-04
Hi,

I recently updated to 11.04, I had the same problem with 10.10 but never bothered to look into fixing it but I was hoping 11.04 would be able to get past this. If I switch my wifi card off when I shutdown/logoff everything is fine but if it's left on then system just hangs and I have to do manually power off.

Anyone have any suggestions on this?

---

### Post by praseodym on 2011-10-04
Please show:

```
lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
```

---

