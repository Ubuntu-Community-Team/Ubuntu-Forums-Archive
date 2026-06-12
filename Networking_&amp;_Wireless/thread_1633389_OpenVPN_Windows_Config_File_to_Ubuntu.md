---
title: "OpenVPN Windows Config File to Ubuntu?"
date: 2010-11-29
forum: Networking &amp; Wireless
---

### Post by bstacker on 2010-11-29
Hello everyone,

So I'm new to OpenVPN and I was just informed yesterday that my school is running an OpenVPN server that I could utilize to access my section of Oracle space from offsite.  The problem I've got is that they only offer config files for Windows and OSX.

I'm wondering if there is a way that I can utilize the data that I "think" is the configuration information.

```
dev tap
remote vpn.xxx.xxxxxx.edu 8000
resolv-retry 60
proto tcp-client
tls-client
auth-user-pass
ca vpnca.crt
tun-mtu 1500
tun-mtu-extra 32
mssfix 1450
pull
comp-lzo

verb 4
```

I also have the xxx.ovpn and vpnca.crt files on a Windows install of a local machine.  Could I apply the information above in conjunction with the files to make some VPN magic happen?

I definitely appreciate any advice!

Thanks!

---

