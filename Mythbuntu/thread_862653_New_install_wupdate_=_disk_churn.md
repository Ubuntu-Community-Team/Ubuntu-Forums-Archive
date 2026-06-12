---
title: "New install w/update = disk churn"
date: 2008-07-17
forum: Mythbuntu
---

### Post by bartt on 2008-07-17
I did a new install of mythbuntu 8.04. Most everything seemed ok at this point, system is quite responsive on the mini-itx board. Tweeked the network settings to get online and got a notice that the updater needed to run. It ran for quite a while and pulled over a couple hundred meg and installed it all. 
After a reboot the disk is churning constantly, and the boot time went from 30 seconds to well over 5 minutes. I have rebooted a couple of times now with the same results. 
There is a repeating pattern to the sound the drive is making while churning. Is there something I can run to tell what it is doing?
Should I just reinstall from scratch?:confused:

---

### Post by superm1 on 2008-07-17
> **bartt said:**
> I did a new install of mythbuntu 8.04. Most everything seemed ok at this point, system is quite responsive on the mini-itx board. Tweeked the network settings to get online and got a notice that the updater needed to run. It ran for quite a while and pulled over a couple hundred meg and installed it all. 
After a reboot the disk is churning constantly, and the boot time went from 30 seconds to well over 5 minutes. I have rebooted a couple of times now with the same results. 
There is a repeating pattern to the sound the drive is making while churning. Is there something I can run to tell what it is doing?
Should I just reinstall from scratch?:confused:
Check your backend log (/var/log/mythtv/mythbackend.log)  That's the most common pointer for errors.  Also look at dmesg and /var/log/messages and /var/log/syslog.

Updates are generally safe to run, but perhaps you got something quirky (in which case if it's discovered, lets get a bug filed and get it fixed).

---

