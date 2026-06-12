---
title: "Wireless stops working after reboot"
date: 2008-12-13
forum: Networking &amp; Wireless
---

### Post by JulesJacobs on 2008-12-13
When I boot up wireless doesn't work (also doesn't show available networks). I have to go to System > Administration > Hardware Drivers. On that window I see that the proprietary "Broadcom STA wireless driver" is disabled. If I enable it wireless still doesn't work, but if I disable it again wireless works! I have to perform this every time I reboot.

Does anyone know what causes the problem and maybe also how to fix it?

Thanks for your help,

Jules

---

### Post by Ayuthia on 2008-12-13
> **JulesJacobs said:**
> When I boot up wireless doesn't work (also doesn't show available networks). I have to go to System > Administration > Hardware Drivers. On that window I see that the proprietary "Broadcom STA wireless driver" is disabled. If I enable it wireless still doesn't work, but if I disable it again wireless works! I have to perform this every time I reboot.

Does anyone know what causes the problem and maybe also how to fix it?

Thanks for your help,

Jules

Please try the following and see if it works:
```
echo wl|sudo tee -a /etc/modules
```
This command will add the wl module to the modules list.  This is the modules list that will load after all the kernel modules have been loaded.

Hope that helps.  If not, please let us know and please post the results of (from the Terminal):
```
lshw -C network
```

---

### Post by JulesJacobs on 2008-12-13
Thanks! That worked! :)

---

