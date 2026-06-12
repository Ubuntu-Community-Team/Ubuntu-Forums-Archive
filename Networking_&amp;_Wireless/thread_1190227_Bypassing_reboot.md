---
title: "Bypassing reboot"
date: 2009-06-17
forum: Networking &amp; Wireless
---

### Post by MissFixIt on 2009-06-17
I made changes to /etc/iftab and I would like to see the changes without having to reboot.  I've tried /etc/init.d/networking to no avail.  Is there a way to bypass a reboot?

---

### Post by synapsys on 2009-06-17
logout/login?

---

### Post by doas777 on 2009-06-17
you may be able to get by with a ```
depmod -a
```

---

### Post by cariboo on 2009-06-17
You can restart networking by running:

```
sudo /etc/init.d/networking restart
```

---

### Post by MissFixIt on 2009-06-18
The version of Ubuntu I have does not use the persistent-network.rules file.  It still uses /etc/iftab.  I'm assigning a  mac address to a specific device name (other than eth*).  This new name does not show up if I run the /etc/init.d/networking command or depmod -a; only when I reboot.  I'm writing a script for these actions and don't want to reboot.

---

