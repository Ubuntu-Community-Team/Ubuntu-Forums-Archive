---
title: "No wireless network on Aspire one D270, running on Ubuntu 10.04 Lucid"
date: 2013-02-11
forum: Networking &amp; Wireless
---

### Post by ra00f on 2013-02-11
Hello,

Somehow, I lost my wireless network access and I couldn't find a solution even after a lot of search.

Here are some info about my system, if that helps.
```
uname -a
Linux kumar-laptop 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010 i686 GNU/Linux

``````
lspci -knn | grep -i net -A4
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
    Kernel driver in use: r8169
    Kernel modules: r8169
02:00.0 Network controller [0280]: Atheros Communications Inc. Device [168c:0032] (rev 01)
03:00.0 Class [ff00]: Realtek Semiconductor Co., Ltd. Device [10ec:5209] (rev 01)

``````
sudo rfkill list

gives nothing
```What should I do?

Any help would be highly appreciated.

Thanks

---

### Post by codemaniac on 2013-02-11
Thread moved to "Networking & Wireless".

---

### Post by ra00f on 2013-02-12
Sorry for a gentle bump, after a day. 
Any suggestions on my issue?

---

### Post by mörgæs on 2013-02-12
First of all I would begin with a fresh install of 12.10. Old software and new hardware is not a good combination.

---

