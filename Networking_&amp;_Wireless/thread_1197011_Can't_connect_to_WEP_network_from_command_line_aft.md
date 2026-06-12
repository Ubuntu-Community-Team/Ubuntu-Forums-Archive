---
title: "Can't connect to WEP network from command line after connecting to WPA network"
date: 2009-06-25
forum: Networking &amp; Wireless
---

### Post by Tomone on 2009-06-25
From the terminal, I can connect to the WEP network and go back and forth between that and the wired connection. But after I connect to the WPA network, I can't re-connect to the WEP network. It looks like it will connect to it, but then it ends up connecting to the WPA network instead. I've been using ifconfig, iwconfig, and dhclient to connect, which works fine as long as I haven't connected to the WPA network since the computer's been on. 
Any ideas?

---

### Post by pytheas22 on 2009-06-25
Try stopping NetworkManager before running the commands to connect to WEP:
```

sudo /etc/init.d/NetworkManager stop
```

NM is probably interfering by trying to connect you to the WPA network.  It doesn't play nicely with other processes that are trying to control network hardware.

---

### Post by Tomone on 2009-06-25
Thanks, that helped me figure it out. I don't have network-manager, but I checked the running processes and found that there were a few instances of wpa_supplicant working. Once I killed those, I could connect to the WEP network.

---

