---
title: "Ubuntu pc not showing up in Windows 7 network"
date: 2011-01-13
forum: Networking &amp; Wireless
---

### Post by Brokenclock on 2011-01-13
I am new to ubuntu and do not know why my Ubuntu 10.10 PC does not show up on my Windows 7 pc's.  All my windows 7 pc's show up on the Ubuntu pc under places> network.  I can access windows 7 shared folders from the Ubuntu PC.  On the windows 7 pc If i use the run command followed by the ip address of the ubuntu then all the shared folders on the ubuntu pc can be accessed.  The problem I am having is that I have to use the Run command from the windows 7 pc to access any thing on the Ubuntu pc.  Is there any way the Ubuntu pc will show up as computer on the windows 7 pc under network?  Thanks in advance.

---

### Post by foxmulder881 on 2011-01-13
You need to install samba.

```
sudo apt-get install samba
```

---

### Post by Brokenclock on 2011-01-13
I have already installed Samba.  I can access folders both ways. 
the problem is Ubuntu pc does not show under network on the windows 7 pc.  The only way i can access ubuntu pc from windows pc is by using Run 192.168.xxx.xxx from the windows  7 pc.

---

### Post by foxmulder881 on 2011-01-14
Hmmm, odd. As long as you have samba installed and working, I would have thought that's all that was required. That's all I've ever done previously and it works in Windows XP. Windows Vista/7 must be slightly different. Perhaps someone else may be able to help you with W7 networking.

---

### Post by k3vmcd on 2011-07-28
I finally solved it by reducing my Ubuntu computer name to 15 characters or less (the max for the NetBIOS protocol). I also implemented nearly all of the other changes listed here first, though.

---

### Post by rwelsh09 on 2012-10-20
> **k3vmcd said:**
> I finally solved it by reducing my Ubuntu computer name to 15 characters or less (the max for the NetBIOS protocol). I also implemented nearly all of the other changes listed here first, though.

Thanks!

---

