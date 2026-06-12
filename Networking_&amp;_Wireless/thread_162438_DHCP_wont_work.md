---
title: "DHCP wont work"
date: 2006-04-19
forum: Networking &amp; Wireless
---

### Post by ubuntukid on 2006-04-19
I'm having trouble using DHCP. It never seems to manage to connect to the internett via dhcp, but if I go to the other room and nick the IP address from my eMac and use that then it connects to the internet strait away and the Mac requests a new IP which it gets. This works but it's very anoying. Why wont it work with DHCP?

---

### Post by mandrakethepenguin on 2006-04-20
I've seen people with similar problems.  In a terminal, type in:```
sudo dhclient
```If you can access the internet after that, then follow these steps to activate DHCP at user login.

In a terminal type```
sudo visudo
``` and at the end of that sudoers file, type this in:```
your_username ALL = NOPASSWD: /sbin/dhclient
```Save the document (Ctrl + O) then exit (Ctrl + X).  Exit the terminal, then go to **System -> Prefrences -> Sessions**.  Add this command to **Startup Progams**```
gnome-terminal -x sudo dhclient
```

You should be able to access the internet after doing this.

---

