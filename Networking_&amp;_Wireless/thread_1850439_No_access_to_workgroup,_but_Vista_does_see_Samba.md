---
title: "No access to workgroup, but Vista does see Samba"
date: 2011-09-26
forum: Networking &amp; Wireless
---

### Post by paul1149 on 2011-09-26
Hi,

I've got an ubuntu 10.04 install on an older box, running ethernet to my LAN via a router. I'm on a full administration account, whose login is a clone of a local Vista account (necessary for Windows workgroup sharing).

Vista can access my samba shares beautifully - praise the Lord. But ubuntu doesn't get to first base accessing the workgroup.

I looked in the router, and my ubuntu hostname is picked up perfectly in the clients list.

I just fired up an XP box, to make sure that Vista's permissions are not the issue, and ubuntu still cannot access the workgroup. So it seems the problem resides with my ubuntu settings.

I also discovered that enabling IPv6 kills the ethernet connection. I suppose that's a function of my older hardware?

---

### Post by linuscat on 2011-10-14
I have the same problem, I can share files Vista to XP, XP to Vista, Vista to Win7, Win7 to Vista and Vista to UBUNTU. I Have tried 3 Linux distributions and have not shared from linux to vista yet. I think this is a Vista problem or the IPv6 connection setup. I have not found any help with the IPv6 setup.:sad:

---

### Post by julio8a on 2011-10-18
Hi, I have a Xubuntu 11.10 installed in my desktop pc, and windows vista in my laptop.  Installing Samba and following all setup procedure of the samba manual was easy but I can't see folders from Xubuntu on my laptop running windows vista.

With Gigolo software I can see and access my folders in my laptop.

The same thing happens with another laptop running windows 7.

I quit all samba pkg and then I install it again, but I have the same problem.

Is there anybody can help following a procedure step by step?   I am new using linux systems, and of course, I don't know about commands and all other syntaxis issues.

Thanks a lot!

---

### Post by sandrodz on 2011-10-20
> **julio8a said:**
> Hi, I have a Xubuntu 11.10 installed in my desktop pc, and windows vista in my laptop.  Installing Samba and following all setup procedure of the samba manual was easy but I can't see folders from Xubuntu on my laptop running windows vista.

With Gigolo software I can see and access my folders in my laptop.

The same thing happens with another laptop running windows 7.

I quit all samba pkg and then I install it again, but I have the same problem.

Is there anybody can help following a procedure step by step?   I am new using linux systems, and of course, I don't know about commands and all other syntaxis issues.

Thanks a lot!

Did you map drive?

On my win7 laptop samba doesn't automagically appear like it does in ubuntu laptop / under networks.

In win you have to map the drive, or add it as a network drive.

Go to my computer and there right click add - type in your server IP \\ip\sharename

So at my house I've something lilke this \\10.532.2.3\shared

---

