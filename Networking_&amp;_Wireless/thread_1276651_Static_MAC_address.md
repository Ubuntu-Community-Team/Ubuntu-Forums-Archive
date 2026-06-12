---
title: "Static MAC address"
date: 2009-09-27
forum: Networking &amp; Wireless
---

### Post by therussianjig on 2009-09-27
Hi, There is a problem with my Ethernet Adapter where it cannot retain a MAC address. On my schools network we must log in with a constant MAC in order to access the network. In windows this is not a problem because i was able to easily spoof it. But on Ubuntu every time I log in it creates a new Ethernet Adapter and assigns it a random MAC address. I have tried changing the MAC address but I cannot find a way to make it persistent because every time I log in, a new adapter is created. Any Ideas?
Thanks

---

### Post by cariboo on 2009-09-27
If you need to register a mac address, why are you spoofing it? Just register your mac address, it will be the same whether running Windows or Linux.

---

### Post by therussianjig on 2009-09-27
I am spoofing my MAC address because it resets every time my computer restarts as there is a problem with NVIDIA adapter where the default MAC address is 00-00-00-00-00.

---

### Post by beastrace91 on 2009-10-13
Try the following in terminal: ```
ifconfig eth0 down
ifconfig eth0 hw ether 00:11:22:33:44:55
ifconfig eth0 up
```

~Jeff

---

