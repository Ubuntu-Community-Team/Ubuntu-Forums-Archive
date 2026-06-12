---
title: "I cannot use wired lan"
date: 2010-01-23
forum: Networking &amp; Wireless
---

### Post by Tmora on 2010-01-23
Please help me. I am not familiar with device driver issue.
I purchased Toshiba Satellite P500. I cannot use wired lan. Ubuntu cannot recognize Ethercard.
My Ether chip is made Attansic Technology Corp. So according the previoius trouble shoot, I got and compiled the latest device driver of the chip, atl1e.
I add it to kernel by modprobe atl1e.
I removed the old module, atl1c by modprobe -r atl1c, and put is blacklist file.
I checked modules running by lsmod, and I confirmed atl1e is loaded and atl1c is not loaded. But Ubuntu still cannot recognized eth0. I checked it by ifconfig -a, I could see only "lo".
I checked pci devices by lspci -vvnn, and I found the following lines,
   Capabilities: <access denied>
   Kernel modules: atl1c
I suppose Attansic's ether chip still try to use removed atl1c module.
If someone knows what should I do, please tell me.
Thank you very much.

---

### Post by Iowan on 2010-01-23
I know VERY little about drivers - so this is just musing: I wonder if it could be a permissions problem with the new driver you built.

---

### Post by Tmora on 2010-01-23
> **Iowan said:**
> I know VERY little about drivers - so this is just musing: I wonder if it could be a permissions problem with the new driver you built.

  Before I remove the ctl1c module, lspci tells me that ctl1c module are accepted. So I suppose this problem is not related to issues about permission problem.
  But I will check it. Thank you very much.:P

---

### Post by gnometorule on 2010-01-23
I haven't successfully installed an ethernet driver yet as mine luckily worked. But maybe something in this very long thread (which also cross-references others) might help you:

[http://swiss.ubuntuforums.org/showthread.php?t=1276211](http://swiss.ubuntuforums.org/showthread.php?t=1276211)

---

### Post by Tmora on 2010-01-23
> **gnometorule said:**
> I haven't successfully installed an ethernet driver yet as mine luckily worked. But maybe something in this very long thread (which also cross-references others) might help you:

[http://swiss.ubuntuforums.org/showthread.php?t=1276211](http://swiss.ubuntuforums.org/showthread.php?t=1276211)

Thank you. I will read the reference above.

---

