---
title: "ndiswrapper causes kernel panic"
date: 2006-06-07
forum: Networking &amp; Wireless
---

### Post by ignavia on 2006-06-07
After I installed my Zonet wireless card with ndiswrapper, it worked great after a reboot. But after a second reboot, the system never started. I restarted with the NIC removed, then again with it reinserted, and it was fine. Then it quit working again, and I started getting kernel panic messages.

I gave up and reinstalled Xubuntu. Now I want to set my card up again with ndiswrapper, but I want to do it without problems. On boot, I can see messages about errors loading mrv8k, so I think I probably need to blacklist that. How do I do that?

Any help is appreciated. Thanks.

---

### Post by DarthMandeep on 2006-06-07
You can blacklist a module by adding "blacklist modulename" to the /etc/modprobe.d/blacklist file.

---

### Post by ignavia on 2006-06-07
Thanks. I searched, but everything I found just said to blacklist it without giving any instructions.

---

### Post by nzruss on 2006-06-07
you can also use this command:

```

echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist

```

The echo just repeats the text between the ' ' and the | (pipe) pipes it to the end (-a = append) of the blacklist file in the modprobe.d directory.

---

