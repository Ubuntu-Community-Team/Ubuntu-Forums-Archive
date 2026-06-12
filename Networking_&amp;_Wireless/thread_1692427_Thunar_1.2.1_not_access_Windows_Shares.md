---
title: "Thunar 1.2.1 not access Windows Shares?"
date: 2011-02-21
forum: Networking &amp; Wireless
---

### Post by nhtrader on 2011-02-21
Xubuntu 10.10
xfce 4.8.0
thunar 1.2.1

I'm trying to access my windows shares but am having problems.

I select thunar's Network Icon
I see 2 items:
1. router
2. windows network

I select windows network
I now see 2 items
1. WG1
2. WG2

I select WG1

Here's the error message
Failed to open "WG1"
Failed to retrieve share list from server

How do I begin figuring this out?

I have the following PCs running and connected to the network:
1. kubuntu 10.04
2. Mythbuntu 10.10
3. Xubuntu 10.10 (I'm using thunar here)
4. Win7
5. WinXP

---

### Post by Keiran230 on 2011-02-21
Do you  have Samba installed and configured on that machine? Windows uses the SMB protocol to transfer file shares over the network. Linux and MacOS use NFS. If you install and configure Samba, Linux will support SMB too.

---

### Post by nhtrader on 2011-02-22
> **Keiran230 said:**
> Do you  have Samba installed and configured on that machine? Windows uses the SMB protocol to transfer file shares over the network. Linux and MacOS use NFS. If you install and configure Samba, Linux will support SMB too.


No. I just checked. My Xubuntu 10.10 with xfce 4.8.0 does not. I use the following command:

sudo su
ps aux | grep mbd

(I'm looking for smbd and nmbd in the output and I didn't see them.)

It's interesting how each flavor of ubuntu implements networking. With kubuntu and ubuntu samba is automatically active, apparently not with Xubuntu.

---

### Post by dmizer on 2011-02-22
Applications > System > Gigolo

Configure your shares. Gigolo will reside in your notification bar and you can make shortcuts which are accessibile in Thunar.

---

### Post by nhtrader on 2011-02-23
I'll check out gigolo.

---

