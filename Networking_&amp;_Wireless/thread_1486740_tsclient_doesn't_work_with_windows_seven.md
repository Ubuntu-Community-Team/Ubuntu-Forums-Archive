---
title: "tsclient doesn't work with windows seven"
date: 2010-05-18
forum: Networking &amp; Wireless
---

### Post by hardhu on 2010-05-18
Hello everybody,
I am using Lynx 64-bit, and I am trying to use Terminal Server Client to connect to another pc in my lan with Windows 7 Ultimate 64-bit. However I always get this error: Connection reset by peer. Even if I launch tsclient using sudo things don't change.
Instead everything works if I connect to another pc in the lan which is running Windows XP Professional.

Can anybody help me?

---

### Post by fix_ on 2010-05-18
Could be a windows firewall problem - you need to create an exception in Windows Firewall console (Control Panel) to allow connections to RDP. Check the port state with  (replace ip with yours)

```

nmap 192.168.1.10 -p 3389

```

If host will reply you with something like this, then the service is not running or firewall is blocking inbound RDP (tsclient) traffic. 
```

PORT     STATE SERVICE
3389/tcp closed  ms-term-serv

```

---

### Post by hardhu on 2010-05-18
> **fix_ said:**
> Could be a windows firewall problem - you need to create an exception in Windows Firewall console (Control Panel) to allow connections to RDP. Check the port state with  (replace ip with yours)

```

nmap 192.168.1.10 -p 3389

```

If host will reply you with something like this, then the service is not running or firewall is blocking inbound RDP (tsclient) traffic. 
```

PORT     STATE SERVICE
3389/tcp closed  ms-term-serv

```


I have managed it to work: the problem was not with firewall (the related port was open) but with authentication. In fact, in remote desktop settings in Seven, I had set "Allow connections only from computers running Remote Desktop with Network Level Authentication". Changing it to "Allow connections from computers running any version of Remote Desktop" make it to work with Lynx too.

---

