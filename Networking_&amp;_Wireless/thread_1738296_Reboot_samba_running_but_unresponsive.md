---
title: "Reboot: samba running but unresponsive"
date: 2011-04-24
forum: Networking &amp; Wireless
---

### Post by doas777 on 2011-04-24
I am running a server semi-headless (desktop installed, but usually I connect via ssh/freenx) on my network. after rebooting the box, the samba service will not respond to clients, until I login over nx, and restart samba with 'sudo service smbd restart'. I have it rigged via startup applications, so the command runs on first login, but I would really prefer it come online on boot even if I'm not there to logon. 

I wrote a quick script to enumerate the status of the network services. here is the output right after a reboot. I ran the script from ssh, before starting a desktop session with nx.

```

Checking status of network services
Named Status:
 * bind9 is running

UFW Status:
Status: active

To                         Action      From
--                         ------      ----
53/udp                     ALLOW       Anywhere
192.168.xxx.yyy 135,139,445/tcp ALLOW       192.168.xx.0/24
192.168.xxx.yyy 137,138/udp  ALLOW       192.168.xx.0/24
192.168.xxx.yyy 22/tcp       ALLOW       192.168.xx.0/24
127.0.0.1                  ALLOW       127.0.0.1

Samba Status:
nmbd start/running, process 1832
smbd start/running, process 1163

```so, it looks to me like bind is up, ufw is loaded with the correct rules to allow, and samba/winbind are running, but samba will not respond to clients.

if I rerun the script after logging in to the desktop, the only thing different is the PID for smbd. 

any ideas on how I can get it to load and run without logging in?

---

### Post by doas777 on 2011-04-26
bump

---

### Post by doas777 on 2011-04-27
no love huh?

---

### Post by Morbius1 on 2011-04-27
The only thing I can think of is to force samba to start after you know the network is up:

Create a little script:
```
gksu gedit /etc/network/if-up.d/sambaup
```With this content:
```
#!/bin/sh
service smbd restart
```Make the file executable:
```
sudo chmod +x /etc/network/if-up.d/sambaup
```Anything in if-up.d will run ( as root ) only after the network is up which is one of the last things that happens in a boot sequence..

---

### Post by doas777 on 2011-04-27
Thanks, i will try that tonight. may be just the trick.

---

### Post by doas777 on 2011-04-28
Works like a Charm! Thanks Morbius!

---

