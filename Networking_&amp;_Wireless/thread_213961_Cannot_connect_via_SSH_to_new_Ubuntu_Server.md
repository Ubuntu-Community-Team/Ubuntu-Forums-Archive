---
title: "Cannot connect via SSH to new Ubuntu Server"
date: 2006-07-12
forum: Networking &amp; Wireless
---

### Post by beatyou on 2006-07-12
I've recently installed Ubuntu 6.06 Server. I'm having a frustrating problem connecting to the new install via SSH. When I try to connect to the server on my client machine it just hangs after I attempt to connect, what did I miss here? I am on the same network as the server and I can ping it's IP fine. Please advise, thanks.
[LIST]
[*]Verified OpenSSH server is running on my server
[*]did nmap 192.168.1.1 and found port 22 open ready for SSH connections
```

corey@bluetoshiba:~$ nmap mankind
Interesting ports on mankind (192.168.1.1):
(The 1673 ports scanned but not shown below are in state: closed)
PORT   STATE SERVICE
22/tcp open  ssh

```
[*]Connected locally through the SSH while on the server just to verify it was running/working, logged in fine.
[/LIST]

I've tried almost every way I can think of to connect but they all just hang and never go through:
```

corey@bluetoshiba:~$ ssh mankind
corey@bluetoshiba:~$ ssh root@mankind
corey@bluetoshiba:~$ ssh 192.168.1.1
corey@bluetoshiba:~$ ssh root@192.168.1.1

```

I have even mapped the hostname mankind to the IP address 192.168.1.1 in /etc/hosts, see below.
```

127.0.0.1 localhost bluetoshiba
192.168.1.1 mankind mankind
# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

If anyone needs any more info please ask. Thanks.

---

### Post by MrHorus on 2006-07-12
Are the usernames the same?
If not you will need the -l flag.
```
ssh bob.wibble.org -l username
```

---

### Post by beatyou on 2006-07-12
MrHorus,

I tried that as well as adding user@host, such as corey@192.168.1.1 corey@mankind etc.

Is there any ssh configuration file where I can add my client as a "trusted client" or anything. It seems like the OpenSSH server is rejecting my connection for some reason.

---

