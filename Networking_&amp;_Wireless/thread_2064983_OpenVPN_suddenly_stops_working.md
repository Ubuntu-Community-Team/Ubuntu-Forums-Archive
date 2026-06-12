---
title: "OpenVPN suddenly stops working"
date: 2012-09-30
forum: Networking &amp; Wireless
---

### Post by jomplox on 2012-09-30
I'm running Ubuntu 10.10 on a OpenVZ VPS with TUN/TAP enabled. Months ago I succesfully configured a openvpn server on my VPS.
Two days ago there was a power outage on my host's data center which resulted in downtime. After everything came back online my openvpn server failed to start.


**This is the /var/log/openvpn.log**
```
Sun Sep 30 19:47:53 2012 OpenVPN 2.1.0 i686-pc-linux-gnu [SSL] [LZO2] [EPOLL] [PKCS11] [MH] [PF_INET6] [eurephia] built on Jul 12 2010
Sun Sep 30 19:47:53 2012 NOTE: the current --script-security setting may allow this configuration to call user-defined scripts
Sun Sep 30 19:47:53 2012 /usr/bin/openssl-vulnkey -q -b 1024 -m <modulus omitted>
Sun Sep 30 19:47:53 2012 Note: Cannot open TUN/TAP dev /dev/net/tun: Permission denied (errno=13)
Sun Sep 30 19:47:53 2012 Note: Attempting fallback to kernel 2.2 TUN/TAP interface
Sun Sep 30 19:47:53 2012 Cannot allocate TUN/TAP dev dynamically
Sun Sep 30 19:47:53 2012 Exiting
```

**This is the ourput for cat /dev/net/tun**
```
root@vps:~# cat /dev/net/tun                      
cat: /dev/net/tun: File descriptor in bad state
```

Any help is greatly appreciated!

---

