---
title: "Wireless is requesting access code every minute"
date: 2012-05-07
forum: Networking &amp; Wireless
---

### Post by marcoav on 2012-05-07
Hi,
I just upgrade my HP Mini 1120 LA netbook to Ubuntu12.04 LTS, after that the wireless conection is requesting the access code to the hot spot every minute.

How can it be solved?

---

### Post by brainwash on 2012-05-08
Does the hot spot support IPv6? If yes, disabling IPv6 in the network manager or just deactivating the IPv6 Privacy Extensions (configuration file) might solve the problem.

You can check, if you are using a temporary IPv6 address and its lifetime (valid_lft, prefered_lft), by running these commands:
```
ifconfig
ip addr
```

---

