---
title: "RSA Authenticity of SSH via IP vs hostname"
date: 2009-11-09
forum: Networking &amp; Wireless
---

### Post by Spectre5 on 2009-11-09
I have two computers currently setup, both with static IP's and connected to the internet via a router + cable model.

Normally, to log into ssh, I use the following (filling in 'X' of course):
```
ssh -p1080 user@192.168.1.X
```

I'd like to change this to use a hostname rather then the local IP:
```
ssh -p1080 user@hostname
```

So I added the following line to the connecting computers /etc/hosts file:
```
192.168.1.X hostname
```

This seems to work...when I connect with the hostname, it does connect to the second computer, but I get a message about the RSA Key:
```
The authenticity of host '[hostname]:1080 ([192.168.1.X]:1080)' can't be established.
RSA key fingerprint is FI:NG:ER:PR:IN:T
Are you sure you want to continue connecting (yes/no)?
```

When I use the IP to connect, I do not get this message.  It should be connecting to the same computer, so why do I get the RSA key error when connecting using the hostname, but not when using the IP?

---

### Post by fargle on 2009-11-10
OpenSSH stores the keys it knows in ~/.ssh/known_hosts, and it does it based on the name you typed to get there, not always by IP address.

In short, SSH wants to remember a key for each way you access the machine, so this is expected behavior.  Just check the fingerprint matches and accept the key, and if it bugs you, connect to the host the same way each time, not sometimes by IP and sometimes by hostname.

---

### Post by Spectre5 on 2009-11-11
> **fargle said:**
> OpenSSH stores the keys it knows in ~/.ssh/known_hosts, and it does it based on the name you typed to get there, not always by IP address.

In short, SSH wants to remember a key for each way you access the machine, so this is expected behavior.  Just check the fingerprint matches and accept the key, and if it bugs you, connect to the host the same way each time, not sometimes by IP and sometimes by hostname.

I plan to only use hostnames now, thanks for the info.

---

