---
title: "Firewall as daemon"
date: 2009-10-13
forum: Networking &amp; Wireless
---

### Post by Legendário on 2009-10-13
Hi,

I saw at firestarter FAQ the way to auto start firestarter with the computer, but it requires you to add it to the gnome session preferences for it to start at logon.

Since this is a personal configuration, I believe it works only for the programmed login.

Is there a way to start a firewall independent from the user who is login on the machine? Is there a firewall that works as a daemon?

Thanks for the help.

---

### Post by BQAggie2006 on 2009-10-13
Check out Ubuntu's default firewall UFW (the Uncomplicated FireWall). If you are looking for a way to graphically manage it, there is a GUI package gufw.

---

### Post by Legendário on 2009-10-13
> **BQAggie2006 said:**
> Check out Ubuntu's default firewall UFW (the Uncomplicated FireWall). If you are looking for a way to graphically manage it, there is a GUI package gufw.

But does it work as a daemon??? Firestarter is just a gui for iptables isn't it?

---

### Post by BQAggie2006 on 2009-10-13
It appears that once UFW is enabled, it starts during the system startup process.

---

