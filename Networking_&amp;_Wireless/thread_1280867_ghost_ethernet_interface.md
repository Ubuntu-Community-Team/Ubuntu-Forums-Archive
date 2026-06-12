---
title: "ghost ethernet interface"
date: 2009-10-02
forum: Networking &amp; Wireless
---

### Post by renebs on 2009-10-02
Hi,

I have a ghost interface eth0 for my ethernet card that is not "mapped" to any hardware. (I explain why bellow). I would like to delete such interface, how can I do that?

Thanks,
===== the story =====
I recently had to send my thinkpad Sl400 (with about 6months of use) under warranty to fix a glitch.
They replaced my motherboard and with it the ethernet card came with it. It took me a couple of days to realize the change. I noticed while watching the boot up messages and:
"eth0 failed to start message" showed up.

So, not only I found out that I had a new mother board, but I realized how smooth Ubuntu linux is working. It had detected the "new hardware" and, in particular, assigned the new ethernet card to interface eth1, as it stands now. No configuring problems, just like when I had a fresh install. 

Btw, if you own a lenovo laptop, it's good to know that you do not need to send your harddrive to them (also good to know is that the SL400 rescue disks will erase ALL partitions on your system! That's what "factore" state really means, deleting all partitions, the funny thing is that while running such "rescue disks" there is no warning, partition xyz will be deleted, do you want to proceed?)

---

### Post by renebs on 2009-10-02
This solution provided by cement_head worked fine. 
Take a look: [http://ubuntuforums.org/showthread.php?t=1199030&highlight=move+eth1+eth0](http://ubuntuforums.org/showthread.php?t=1199030&highlight=move+eth1+eth0)

---

### Post by renebs on 2009-10-02
This solution provided by cement_head worked fine. 
Take a look: [http://ubuntuforums.org/showthread.php?t=1199030&highlight=move+eth1+eth0](http://ubuntuforums.org/showthread.php?t=1199030&highlight=move+eth1+eth0)

---

