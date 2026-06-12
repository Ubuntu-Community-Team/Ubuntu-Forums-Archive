---
title: "How to share files with windows 7 with LAN"
date: 2012-07-16
forum: Networking &amp; Wireless
---

### Post by Gauravs90 on 2012-07-16
Hi.

I want to connect to windows 7 with LAN but it is not connecting and I'm not able to share the files.

Pls help.

---

### Post by ajgreeny on 2012-07-16
You need samba on your ubuntu box configured to share with the windows box.

I have never used samba and don't have windows, so can't help with more details.
[https://help.ubuntu.com/community/Samba](https://help.ubuntu.com/community/Samba)

---

### Post by sudodus on 2012-07-16
You need to decide which computer(s) should be server(s) (allowing the other computers to log in remotely either to share files or run programs).

***Samba*** is one alternative. ***SSH*** (secure shell) is another alternative.

I would install the SSH service [FONT="Courier New"][SIZE="3"]sshd[/SIZE][/FONT] in Ubuntu
[[COLOR="Red"]_https://help.ubuntu.com/10.04/serverguide/openssh-server.html_[/COLOR]]("https://help.ubuntu.com/10.04/serverguide/openssh-server.html")

and install ***WinSCP*** in your Windows computers to log in to share files in what is now your Ubuntu server.

Finally be aware of the security issues: I think SSH can be configured to be more secure than Samba.
[[COLOR="red"]_https://wiki.ubuntu.com/BasicSecurity_[/COLOR]]("https://wiki.ubuntu.com/BasicSecurity")

---

### Post by OM55 on 2012-07-16
In my opinion Samba server on the Ubuntu machine will be the easiest to set up (and cheapest) between the options.
You can install it from the Software Center or just type in terminal:
```
sudo apt-get install samba
```

Then lunch the Samba application (the software center will show you its name and where it was installed) and add specific shares and usernames allowed to access them.
Remember that you can share only folders that you are the owner. So will not be able to share something that is located under /media for example.

---

