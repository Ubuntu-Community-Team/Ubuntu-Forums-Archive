---
title: "OpenVPN connectivity test failure"
date: 2012-05-24
forum: Networking &amp; Wireless
---

### Post by dyrer on 2012-05-24
Hello
I have download from opevpn.net server file to to setup a vpn network
Admin and client connection works fine, but i cannot connect to internet through VPN, and connectivity test failed
Any ideas?

---

### Post by eleftg on 2012-05-24
Have you installed openvpn from the official repository or have you compiled it from source?

---

### Post by dyrer on 2012-05-24
from official repository openvpn.net

---

### Post by eleftg on 2012-05-24
By asking if you have it installed from the official repository I meant the ubuntu official repository and not the supplied packages from openvpn.net.

Anyway, can you elaborate on what exactly do you want to achieve with openvpn? Do you have problems making it work through Network Manager or through the command line? Do you run openvpn as root?

---

### Post by dyrer on 2012-05-24
I removed openvpn from openvpn.net and install from ubunutu repository, how now can configure from the beginning Openvpn?

---

### Post by eleftg on 2012-05-24
I suppose you have a .ovpn or a .conf configuration file ready to work, isn't it? Then just run in terminal:

```
sudo openvpn /path/to/your/config/file.conf
```

---

