---
title: "Managing Ethernet and Wireless connections"
date: 2009-11-26
forum: Networking &amp; Wireless
---

### Post by Tozzonator on 2009-11-26
Is there a way (preferably via GUI) to choose the priority of wired and wireless connections, since my Xbox is connected to my laptop via the Ethernet and I want to connect to the internet via Wireless, however 9.10 likes to look for an internet connection in my Xbox since it chooses wired over wireless.  Can anyone help?

---

### Post by SteveDee on 2009-11-27
> **Tozzonator said:**
> Is there a way (preferably via GUI) to choose the priority of wired and wireless connections, since my Xbox is connected to my laptop via the Ethernet and I want to connect to the internet via Wireless, however 9.10 likes to look for an internet connection in my Xbox since it chooses wired over wireless.  Can anyone help?

I had a similar requirement where I needed Wifi internet access and a hard link between 2 workstations for fast file transfer.

I installed the gnome-network-admin (not standard on 9.xx) as per; [https://help.ubuntu.com/community/NetworkAdmin](https://help.ubuntu.com/community/NetworkAdmin) and setup the wired interface with a static IP with a different number sequence (i.e. 200.1.1.x for wired, 192.168.0.x for wifi).

This works, but to use the wired connection with Nautilus you have to enter the IP address of the remote device in Location box; smb://200.1.1.2

---

