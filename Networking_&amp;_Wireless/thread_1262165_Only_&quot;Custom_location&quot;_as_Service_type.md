---
title: "Only &quot;Custom location&quot; as Service type"
date: 2009-09-09
forum: Networking &amp; Wireless
---

### Post by avaldi on 2009-09-09
Hi everybody,

I'm writing here to ask you a help.
I installed Ubuntu 9.04 this morning and everything looked to work correctly.
Now I'm trying to connect to a Windows share through the "Connect to Server" dialog but when I attempt to choose "Windows share" as a Service type I cannot find it, I can only choose "Custom location", nothing else.

I tried to connect directly writing the address in Nautilus like "smb://xxx.xxx.xxx.xxx", but I received the message:

> "Could not find XXX."
Please check the spelling and try again.The same if I try to access at "Network" places, I get back:
> "Could not display "network:///"
Nautilus cannot handle "network" locations.Anybody experienced something similar? Any advice?

Thank you very much.
Andrea

---

### Post by benchMarc on 2010-01-23
Same problem here.... Suddenly ubuntu doesn't recognize my usb stick, and i only get "custom location" in the places -> connect to server.

What i did before when everything worked. I connect to an FTP, and my usb stick also got mounted automatically. Before i rebooted i unmounted the FTP mount it automatically made, and the usb mount. After the reboot, i got the problem.

---

### Post by jkwinn on 2010-08-13
I had the same issue... turns out I uninstalled gvfs-backends due to iPhone issues.  Reinstalling seems to fix the issue.

```
$ sudo apt-get install gvfs-backends
```

---

### Post by hesamd on 2010-09-22
> **jkwinn said:**
> I had the same issue... turns out I uninstalled gvfs-backends due to iPhone issues.  Reinstalling seems to fix the issue.

```
$ sudo apt-get install gvfs-backends
```



This really worked thanks.

---

### Post by emeraldinspirations on 2010-11-16
This just happened to me too.  The fix works.  Any idea on what might cause it, I didn't uninstall anything.

---

