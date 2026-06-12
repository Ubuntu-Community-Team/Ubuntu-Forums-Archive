---
title: "OpenVPN failing to connect"
date: 2011-08-03
forum: Networking &amp; Wireless
---

### Post by danls on 2011-08-03
I recently re-installed Ubuntu 11.04.  Previously, I had openVPN client set up and it connected fine.  After re-installing ubuntu, I am unable to connect to the VPN server.

I imported the configuration, keys, and certificates just fine.  But when I use Network Manager to connect to the VPN, it says "VPN Connection Failed".

Checking my syslog, I see the following output:

> Aug  3 11:57:11 BlackBox NetworkManager[1061]: <info> Starting VPN service 'openvpn'...
Aug  3 11:57:11 BlackBox NetworkManager[1061]: <info> VPN service 'openvpn' started (org.freedesktop.NetworkManager.openvpn), PID 2820
Aug  3 11:57:11 BlackBox NetworkManager[1061]: <info> VPN service 'openvpn' appeared; activating connections
Aug  3 11:57:11 BlackBox NetworkManager[1061]: <info> VPN plugin state changed: 1
Aug  3 11:57:11 BlackBox NetworkManager[1061]: <info> VPN plugin state changed: 3
Aug  3 11:57:11 BlackBox nm-openvpn[2823]: OpenVPN 2.1.3 x86_64-pc-linux-gnu [SSL] [LZO2] [EPOLL] [PKCS11] [MH] [PF_INET6] [eurephia] built on Mar 11 2011
Aug  3 11:57:11 BlackBox NetworkManager[1061]: <info> VPN connection '018 us - WASH DC METRO' (Connect) reply received.
Aug  3 11:57:11 BlackBox nm-openvpn[2823]: WARNING: No server certificate verification method has been enabled.  See [http://openvpn.net/howto.html#mitm](http://openvpn.net/howto.html#mitm) for more info.
Aug  3 11:57:11 BlackBox nm-openvpn[2823]: NOTE: the current --script-security setting may allow this configuration to call user-defined scripts
Aug  3 11:57:11 BlackBox nm-openvpn[2823]: Cannot load certificate file /media/Garbage/DropBomb/Documents/computer/Witopia/Daniel_Staples.crt: error:0200100D:system library:fopen: Permission denied: error:20074002:BIO routines:FILE_CTRL:system lib: error:140AD002:SSL routines:SSL_CTX_use_certificate_file:system lib
Aug  3 11:57:11 BlackBox nm-openvpn[2823]: Exiting
Aug  3 11:57:11 BlackBox NetworkManager[1061]: <warn> VPN plugin failed: 1
Aug  3 11:57:11 BlackBox NetworkManager[1061]: <info> VPN plugin state changed: 6
Aug  3 11:57:11 BlackBox NetworkManager[1061]: <info> VPN plugin state change reason: 0
Aug  3 11:57:11 BlackBox NetworkManager[1061]: <warn> error disconnecting VPN: Could not process the request because no VPN connection was active.
Aug  3 11:57:11 BlackBox NetworkManager[1061]: <info> Policy set 'Auto akpress' (wlan0) as default for IPv4 routing and DNS.
Aug  3 11:57:17 BlackBox NetworkManager[1061]: <info> VPN service 'openvpn' disappearedThe "Permission Denied" looks like the problematic part.  I'm not sure what the permission problem is, my keys and certificates all have the correct permissions, as far as I can tell.

Any idea?

---

### Post by Skadork on 2011-08-03
whatever user that openvpn is running at needs to have read perms for that file.  so if the file is 600 or 700 it probably won't work since openvpn usually runs as root.

Can you post the output of the following command?

```
 ll /media/Garbage/DropBomb/Documents/computer/Witopia/Daniel_Staples.crt
```

---

### Post by danls on 2011-08-03
Here is the output: 

> danarky@BlackBox:~$ ll /media/Garbage/DropBomb/Documents/computer/Witopia/Daniel_Staples.crt
-rwxr--r-- 1 danarky danarky 1539 2011-06-04 20:55 /media/Garbage/DropBomb/Documents/computer/Witopia/Daniel_Staples.crt*


---

### Post by Skadork on 2011-08-03
That does look correct. Thank you for posting.  What is the log level in your openvpn config file?  You may need to increase verbosity to get more detail from your log.  Try changing to level 3 or 4 and bouncing openvpn to generate a new log

---

### Post by danls on 2011-08-08
Do you mean the config file for the vpn network I'm trying to connect to, or for the openvpn client in general?  Also, I'm not sure how to find or change the log level of something, how would I do that?

---

### Post by Skadork on 2011-08-09
you can do it from the server or client.

For example, my config file looks something like:

```

log-append servers/openvpn.log
verb 3

```

*log-append* is where it will write the log and it will just keep adding to the end of the log file.  *verb* is the verbosity of the logging - the higher the number the more detail.  3 is a good number for the most common issues that keep a vpn from connecting.

Here's another question - do you have your private key password protected? That may be your issue.

---

### Post by danls on 2011-08-11
Unfortunately I do not manage the servers I am trying to connect to, so I cannot see their config files.  However, I don't see 'log-append' or 'verb' in any of the openvpn config files on my computer, so I'm not sure how to change the verbosity.

Also my keys are not password protected.  The file permissions are -rwxr--r--, both owner and group are "danarky" (my username).

Maybe should I uninstall openvpn, remove any leftover config files, and re-install?

---

### Post by danls on 2011-08-11
ok so i tried re-installing not only openvpn, but network-manager as well.  Still nothing has changed...

---

### Post by danls on 2011-08-11
Figured it out.

My keys & certs were stored on a mounted encfs partition.  For some reason, root cannot access that filesystem, though my normal user can.  I moved the keys & certs to my home directory and everything works fine.

Thanks for the help though!

---

