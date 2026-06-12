---
title: "No ethernet and no wireless"
date: 2011-12-10
forum: Networking &amp; Wireless
---

### Post by JFASI on 2011-12-10
I've got an old Sony Viao computer, and the networking doesn't seem to work. The wireless indicator tells me 'networking is disabled,' even when the wireless switch is set to on. All drivers seem to be installed, and when i do ifconfig -a, I see the wlan0 and eth0 interfaces. This is Ubuntu 10.04.2. 

What gives?

---

### Post by lisati on 2011-12-10
A couple of possibilities come to mind. Have a look at your /etc/network/interfaces file. There should be the following lines in it:

```
auto eth0
iface eth0 inet dhcp
```

---

### Post by JFASI on 2011-12-11
This solved it. For some reason the entries for eth0 and wlan0 were missing. Are there any guides to the things that need to be in place for networking to work? I don't know where to check when things go wrong.

---

### Post by bkratz on 2011-12-11
> **JFASI said:**
> This solved it. For some reason the entries for eth0 and wlan0 were missing. Are there any guides to the things that need to be in place for networking to work? I don't know where to check when things go wrong.



this is relatively old but seems to have the information you require.


[https://help.ubuntu.com/8.04/serverguide/C/network-configuration.html](https://help.ubuntu.com/8.04/serverguide/C/network-configuration.html)

---

