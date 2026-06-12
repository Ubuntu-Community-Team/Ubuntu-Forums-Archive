---
title: "OpenVPN is driving me nuts!!!"
date: 2009-07-03
forum: Networking &amp; Wireless
---

### Post by rip0ff on 2009-07-03
root@ubuntu:/etc/openvpn/easy-rsa/keys# /etc/init.d/openvpn start
 * Starting virtual private network daemon(s)...                              
 *   Autostarting VPN 'server'                                           [fail] 

can someone tell me where i can find the logs for this file?

---

### Post by Sjeti on 2009-07-03
You might just try and start it without a daemon, that way you can get the output when it fails.

I'm not too sure where the log goes, though. It'd be nice to know in the future.

---

### Post by dmizer on 2009-07-03
Since you are trying to start openvpn as a daemon, you will find messages in /var/log/daemon.log

You'll have more luck doing as Sjeti suggests:
```
sudo openvpn /etc/openvpn/server.conf
```

---

### Post by rip0ff on 2009-07-03
> **dmizer said:**
> Since you are trying to start openvpn as a daemon, you will find messages in /var/log/daemon.log

You'll have more luck doing as Sjeti suggests:
```
sudo openvpn /etc/openvpn/server.conf
```
I run the following:

```

modprobe tun
modprobe bridge
sudo openvpn /etc/openvpn/server.conf

```
yields

```

Fri Jul  3 15:17:49 2009 OpenVPN 2.1_rc11 i486-pc-linux-gnu [SSL] [LZO2] [EPOLL] [PKCS11] built on Mar  9 2009
Fri Jul  3 15:17:49 2009 NOTE: when bridging your LAN adapter with the TAP adapter, note that the new bridge adapter will often take on its own IP address that is different from what the LAN adapter was previously set to
Fri Jul  3 15:17:49 2009 NOTE: your local LAN uses the extremely common subnet address 192.168.0.x or 192.168.1.x.  Be aware that this might create routing conflicts if you connect to the VPN server from public locations such as internet cafes that use the same subnet.
Fri Jul  3 15:17:49 2009 Diffie-Hellman initialized with 1024 bit key
Fri Jul  3 15:17:49 2009 WARNING: file 'server.key' is group or others accessible
Fri Jul  3 15:17:49 2009 /usr/bin/openssl-vulnkey -q -b 1024 -m <modulus omitted>
Fri Jul  3 15:17:50 2009 WARNING: file 'ta.key' is group or others accessible
Fri Jul  3 15:17:50 2009 Control Channel Authentication: using 'ta.key' as a OpenVPN static key file
Fri Jul  3 15:17:50 2009 Outgoing Control Channel Authentication: Using 160 bit message hash 'SHA1' for HMAC authentication
Fri Jul  3 15:17:50 2009 Incoming Control Channel Authentication: Using 160 bit message hash 'SHA1' for HMAC authentication
Fri Jul  3 15:17:50 2009 TLS-Auth MTU parms [ L:1574 D:166 EF:66 EB:0 ET:0 EL:0 ]
Fri Jul  3 15:17:50 2009 TUN/TAP device tap0 opened
Fri Jul  3 15:17:50 2009 TUN/TAP TX queue length set to 100
Fri Jul  3 15:17:50 2009 /etc/openvpn/up.sh br0 tap0 1500 1574   init
Fri Jul  3 15:17:50 2009 openvpn_execve: external program may not be called due to setting of --script-security level
Fri Jul  3 15:17:50 2009 script failed: external program fork failed
Fri Jul  3 15:17:50 2009 Exiting

```


_________________________________________SOLVED_______________________



changed my server.conf file

dev tap0
to dev tap1

---

