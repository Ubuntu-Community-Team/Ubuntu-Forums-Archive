---
title: "Windows can't access computer through network"
date: 2010-03-26
forum: Networking &amp; Wireless
---

### Post by Raevan on 2010-03-26
So, I'm trying to set up a network with my windows netbook so the Ubuntu comp can access the internet through the netbook's wireless. Finally got the network set up, but can't access the internet on the Ubuntu comp. Also, the Ubuntu machine can recognize and access the files on the netbook, but the netbook only sees a computer named Owner-a6012abd6 which asks for a password.

The netbook is running Windows XP SP3, with an Atheros AR9285 Wireless Network adapter(internet) and an Atheros AR8132 PCI-E Fast Ethernet Controller. The Ubuntu comp is running Ubuntu 9.04.

---

### Post by Iowan on 2010-03-26
I haven't tried to set up Windows ICS... Apparently, your network configuration works if you can access the netbook files from Ubuntu. 
Check **route -n** to verify the netbook is being used as the gateway. Have you tried pinging Internet (by name and address)? If address is successful, but name is not, there may be a DNS problem (*/etc/resolv.conf* should have addresses for nameservers) 
Did you set up shares on Ubuntu with Nautilus or via */etc/samba/smb.conf*. (files are kept in different places). Probably either way (not absolutely sure about the Nautilus-method) will require Samba server to be installed on Ubuntu. Depending on sharing method, you will *probably* need to set up Samba user and password.

---

