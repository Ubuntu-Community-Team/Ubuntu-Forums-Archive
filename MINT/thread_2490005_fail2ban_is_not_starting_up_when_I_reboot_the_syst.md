---
title: "fail2ban is not starting up when I reboot the system."
date: 2023-08-18
forum: MINT
---

### Post by mmcmonster2 on 2023-08-18
fail2ban doesn't restart when I reboot the system.  Not sure how to set it up to restart when the system comes up.  This is what I have:

$ cat /etc/fail2ban/jail.local
```
[sshd]
enabled = true
bantime  = 10h
port = 0:65535
findtime  = 10m
maxretry = 3
backend = systemd

```

$ sudo systemctl start fail2ban

$ systemctl status fail2ban
```
&#9679; fail2ban.service - Fail2Ban Service
     Loaded: loaded (/lib/systemd/system/fail2ban.service; disabled; vendor preset: enabled)
     Active: active (running) since Fri 2023-08-18 07:50:46 EDT; 14min ago
       Docs: man:fail2ban(1)
   Main PID: 4953 (fail2ban-server)
      Tasks: 5 (limit: 14129)
     Memory: 94.9M
        CPU: 800ms
     CGroup: /system.slice/fail2ban.service
             &#9492;&#9472;4953 /usr/bin/python3 /usr/bin/fail2ban-server -xf start

Aug 18 07:50:46 den systemd[1]: Started Fail2Ban Service.
Aug 18 07:50:47 den fail2ban-server[4953]: Server ready
```

$ sudo reboot 0

$ systemctl status fail2ban
```
&#9675; fail2ban.service - Fail2Ban Service
     Loaded: loaded (/lib/systemd/system/fail2ban.service; disabled; vendor pre>
     Active: inactive (dead)
       Docs: man:fail2ban(1)
```

(I'm cross-posting this to Linux Mint forums, as I am having this problem on Linux Mint v21.2, which is based on Ubuntu.)

---

### Post by coffeecat on 2023-08-18
*Thread moved to **Mint** sub-forum.*

---

### Post by TheFu on 2023-08-18
[https://www.linuxcapable.com/fail2ban-custom-jails-20-example-configurations/](https://www.linuxcapable.com/fail2ban-custom-jails-20-example-configurations/)
has examples.  You probably don't want to list all ports in a specific jail, BTW. I'd remove that line.

```
[sshd]
enabled = true
bantime = 1h
port    = ssh
logpath = %(sshd_log)s
backend = %(sshd_backend)s

```

The port above does a lookup in /etc/services to get the port.  If you've moved the sshd port somewhere else, then you'll want a specific number, not a range.
is all I have in mine.

---

