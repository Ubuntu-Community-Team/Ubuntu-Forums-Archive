---
title: "issues with rtl8211CL chipset"
date: 2011-04-26
forum: Networking &amp; Wireless
---

### Post by jonasg on 2011-04-26
Hello,

I have a ZOTAC 9300-itx motherboard with an on board NIC. I can identify it as a rtl8211CL .


I had no troubles so far with this hardware. I installed ubuntu (about a year ago) and it has been working fine untill now.

But now the NIC doesn't respond anymore. I tried modprobe but there seems to be no NIC driver loaded.

I read somewhere that forcedeth (the NVIDIA opensource driver) should be loaded for this NIC to work. But this doesn't seem to be true in my case.

Next I ran lshw -class network

which doesn't return anything, so there is no NIC present according to ubuntu.

Can anyone guide me to a solution to this problem ?

Regards,

Jonas.

---

