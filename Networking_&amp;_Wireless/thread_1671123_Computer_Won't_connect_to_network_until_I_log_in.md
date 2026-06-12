---
title: "Computer Won't connect to network until I log in"
date: 2011-01-19
forum: Networking &amp; Wireless
---

### Post by EienTatsu on 2011-01-19
My desktop doesn't seem to be connecting to the network until I login. This creates a problem if I'm trying to ssh in after a reboot. It's a wired connection. Any ideas?

edit: sorry my internet lagged and the thread got copied

---

### Post by EienTatsu on 2011-01-19
I hate to bump but does anyone think that the bast idea is to just make a bash script or is there a setting somewhere?

---

### Post by redmk2 on 2011-01-20
> **EienTatsu said:**
> My desktop doesn't seem to be connecting to the network until I login. This creates a problem if I'm trying to ssh in after a reboot. It's a wired connection. Any ideas?

edit: sorry my internet lagged and the thread got copied

My guess is you are using Network Manager to configure the interfaces.  This means the interface is not up (configured) until you login.  I understand that you can configure the interface *available to all users*, but I have never done that.  

I configure the interfaces via the /etc/network/interfaces file.  I have no Network Manager installed on any Ubuntu host.

---

### Post by EienTatsu on 2011-01-20
> **redmk2 said:**
> My guess is you are using Network Manager to configure the interfaces.  This means the interface is not up (configured) until you login.  I understand that you can configure the interface *available to all users*, but I have never done that.  

I configure the interfaces via the /etc/network/interfaces file.  I have no Network Manager installed on any Ubuntu host.

I checked the available to all users thing and it works now thank you

---

