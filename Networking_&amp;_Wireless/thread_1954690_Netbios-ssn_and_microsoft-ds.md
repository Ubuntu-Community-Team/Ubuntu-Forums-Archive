---
title: "Netbios-ssn and microsoft-ds"
date: 2012-04-08
forum: Networking &amp; Wireless
---

### Post by Hack.The.Pow. on 2012-04-08
Hello all.  I have a question for you.

I was learning about nmap recently and tried running it on my server.  ```
Not shown: 996 closed ports
PORT    STATE SERVICE
22/tcp  open  ssh
80/tcp  open  http
139/tcp open  netbios-ssn
445/tcp open  microsoft-ds

```

I got that output.  I expected the port 22 and 80 to be open.  However I don't know what netbios-ssn and microsoft-ds are.  I read online that they are usually associated with samba.  

I checked and samba was running.  I didn't need it so I uninstalled it with apt-get.  However after a fresh reboot the two services were still running.

Is there any way that I can check why those services are running?  I assume you can do this via netstat but I am not too familiar with that command.

Thanks in advance.

---

