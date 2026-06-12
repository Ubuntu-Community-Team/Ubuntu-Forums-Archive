---
title: "Samba connects one way but not the other"
date: 2010-10-03
forum: Networking &amp; Wireless
---

### Post by Jonny87 on 2010-10-03
Having trouble with samba between my laptop and desktop. both running samba and both have Kubuntu 10:04 installed.

Laptop can connect to the shared folders on my desktop with no trouble. But I can't seem to get my desktop to see the shared folder on my laptop.

Dolphin either says it couldn't connect and that it could be due to a firewall or it says that is timed out. It can't be the firewall as theres none turned on on my laptop and the one on my desktop is set to allow all connections from the laptop, plus I've even tried it with the firewall turned off briefly.

I've tried straight browsing to it, entering "smb://jonny-laptop/Laptop" into the address bar, even smbclient in the terminal.

I've also tried reinstalling the samba packages and reconfiguring the smb.conf file on my laptop from scratch. I'm sure I've set it up the way that I always have. So why won't it work?

Oh and I can't even find it from an WinXP laptop on the same network that can also access the shared folders on the desktop. And the desktop **can **access the shared folders on the WinXP laptop.

---

### Post by luvshines on 2010-10-03
What does this command(run from desktop) say for your laptop shares:

smbclient -L <laptop-ip/server name> -U<valid-user>%<password>

---

### Post by Jonny87 on 2010-10-03
> **luvshines said:**
> What does this command(run from desktop) say for your laptop shares:

smbclient -L <laptop-ip/server name> -U<valid-user>%<password>

> Connection to 192.168.1.65 failed (Error NT_STATUS_UNSUCCESSFUL)

Any ideas?

---

### Post by Jonny87 on 2010-10-03
Does any one have any clue? it would be really useful if I could get this working.

---

### Post by Jonny87 on 2010-10-04
I seem to have solved this issue.

I turned on firestarter on my laptop and allowed my desktop for all connections. and suddenly I was able to connect to my laptop from my desktop.

I would have though though that if firestarter wasn't even tuned on, that anything would have been able to connect.

Is anyone able to explain this?

---

### Post by luvshines on 2010-10-04
Maybe you can try switching firestarter off again and try this command to see if Samba server ports are reachable from your client

nc -zv <server-name> 139

ALSO

nc -zv <server-name> 445

If these fail then swith on firestarter and again give it a try

---

