---
title: "My ethernet interface changes every time I reset"
date: 2009-06-12
forum: Networking &amp; Wireless
---

### Post by Hogashi on 2009-06-12
[COLOR=#204A87]**[SIZE=3] [/SIZE]**[/COLOR][SIZE=3]I wanted to configure static IP and I found a way. It said I have to configure /etc/network/interfaces but it didn't work so I've changed to use wicd. It worked but it couldn't auto detect ethernet interface. Like I said my ethernet interface changes every time I reset my PC. Does anyone know how can I adjust my ethernet interface static so it won't change anymore?[/SIZE]

---

### Post by gradinaruvasile on 2009-06-12
What u mean by changing interface? eth0, eth1 or that u have another ip on every startup?

If u want to have static ip in /etc/network/interfaces, u have to uninstall gnome-network-manager otherwise you may have problems.

---

### Post by Hogashi on 2009-06-12
> **gradinaruvasile said:**
> What u mean by changing interface? eth0, eth1 or that u have another ip on every startup?

If u want to have static ip in /etc/network/interfaces, u have to uninstall gnome-network-manager otherwise you may have problems.
Yes, it increases one by one. Now it's eth15 but after restart it will be eth16.

---

### Post by Iowan on 2009-06-12
I've seen this in another thread (albeit some time ago).  Quick fix was to edit */etc/udev/rules.d/70-persistent-net.rules*.  I don't remember if that solved problem - or just symptoms.

---

### Post by gradinaruvasile on 2009-06-12
This one?
[http://ubuntuforums.org/showthread.php?p=3869356]("http://ubuntuforums.org/showthread.php?p=3869356")

---

