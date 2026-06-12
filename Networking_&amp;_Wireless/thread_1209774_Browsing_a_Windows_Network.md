---
title: "Browsing a Windows Network"
date: 2009-07-10
forum: Networking &amp; Wireless
---

### Post by Mallach Quinn on 2009-07-10
Hello, everybody :D

I'm having an issue with browsing my Windows network with Ubuntu 9.04. I installed and configured Samba and brought online a Samba share that all of my Windows machines can easily access. I then configured my "/etc/nsswitch.conf" file, installed winbind, and restarted the entire network. I still cannot browse my windows shares :mad: I get the error message "Unable to mount location. Failed to retrieve share list from server" after double-clicking on the workgroup in the file browser.

Here's my smbtree output:

```

HOME
    \\LINDA-DESKTOP          Linda's Desktop Computer
Receiving SMB: Server stopped responding
failed negprot
    \\DOUGLAS-LAPTOP         douglas-laptop server (Samba, Ubuntu)
        \\DOUGLAS-LAPTOP\shared files       Shared Files on Douglas's Laptop
        \\DOUGLAS-LAPTOP\IPC$               IPC Service (douglas-laptop server (Samba, Ubuntu))
        \\DOUGLAS-LAPTOP\print$             Printer Drivers

```

---

### Post by superprash2003 on 2009-07-11
does it work when you try accessing via ip? like smb://x.x.x.x ?

---

### Post by coffeecat on 2009-07-11
Useful howto, "How to fix Windows share browsing issues":

[http://ubuntuforums.org/showthread.php?t=1169149](http://ubuntuforums.org/showthread.php?t=1169149)

---

### Post by Mallach Quinn on 2009-07-12
Thanks for the feedback, guys. I'll checkout that HowTo. And, no, I didn't try the IP approach. I'll try that as well.

---

### Post by Mallach Quinn on 2009-07-12
Well, I'm one step closer, but not quite there yet!

I complied with the HowTo posted above and can now see all of the client machines on my network, but I still cannot browse their contents. I get the "Unable to mount location. Failed to retrieve share list from server." error message after double-clicking on any given client. I turned off any firewalls on the other clients to eliminate the firewall factor, but that didn't solve anything.

---

