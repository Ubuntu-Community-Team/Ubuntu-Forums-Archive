---
title: "Unable to mount location failed: to retrieve share list from server"
date: 2010-07-27
forum: Networking &amp; Wireless
---

### Post by pharmankur on 2010-07-27
Hi,
I am having windows LAN at my office (10 Machines), and only my laptop is dual boot (Windows XP & UBUNTU 10.04).
 
Recently from the office network we have upgraded a PC (having Windows XP); and with that upgrade the machine name was changed from **Office3** (Old name) to **Office1** (New Name).
________________________________________________________

Now my issue is while i am in Ubuntu, I can see all the 10 PCs (Including **Office1**) at 
Places --> Network --> Windows Network --> Unique (My office network)

I can open all the other shared PCs e.g. **Office2** / **Office4** etc.

But I CANNOT Open **Office1**. When I try to open it I get the error
**"Unable to mount location failed: to retrieve share list from server"**

Surprisingly, **Office1** user can see and use my shared folders on Ubuntu, but I cannot access to his folders !!! :(
________________________________________________________
While I am in Windows XP, I dont face any issue. Neither any other ppl have any issues in sharing with **Office1**

To the best of my knowledge, this thing has started since we have upgraded the **Office1 **machine

Please help me with solution if any.

Thanx
Ankur

---

### Post by P4man on 2010-07-27
Have you tried connecting by IP ? In nautilus enter
smb://192.168.x.x or whatever the IP of a windows machine with a shared folder. If that works; then it sounds like a wins problem (are you using a wins server?).

Either way, this link may be be very helpful for you:

[http://ubuntuforums.org/showthread.php?t=1169149](http://ubuntuforums.org/showthread.php?t=1169149)

---

