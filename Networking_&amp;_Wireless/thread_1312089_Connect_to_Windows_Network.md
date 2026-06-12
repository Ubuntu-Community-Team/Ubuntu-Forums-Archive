---
title: "Connect to Windows Network"
date: 2009-11-02
forum: Networking &amp; Wireless
---

### Post by CaptainJackOC on 2009-11-02
I am new to Linux and so far I love it.

I need help on 2 items:  

**1:  CONNECT TO WINDOWS NETWORK;** I have a Windows 2008 Server plus 3 PCs on it (Xp, Vista, Win 7) using AD, DNS and DHCP.  I'm trying to find out how I can connect to the network with Ubuntu on my laptop.  Funny thing is I can see only the XP machine when going to the Network area, and a shared network external drive.  I have my printer shared on the Win 7 machine.

**2: SETUP SHARED PRINTER FROM WIN 7 PC;** I hope this can be resolved once I can connect to the other pc's on the network.

Do I need to install **SAMBA **on my Linux laptop?

---

### Post by Iowan on 2009-11-03
> **CaptainJackOC said:**
> Do I need to install **SAMBA **on my Linux laptop? The Samba client should already be installed. The server component is generally only necessary to share files FROM the Ubuntu box... but I'm not sure what AD requirements might be.

I did a search for "help.ubuntu.com active directory" and found some information on [Active Directory]("https://help.ubuntu.com/community/ActiveDirectoryHowto") [winbind]("https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto") and [likewise]("http://likewise.com/products/likewise_open/index.php?utm_source=googleold&utm_medium=cpc&utm_keyword=ubuntu%20directory%20active&_kk=ubuntu%20directory%20active&_kt=e3b12ec4-d0d9-419b-b208-d6e6fe303b67")

---

### Post by rumentab on 2009-12-24
I'm having the same problem. My Ubuntu on the laptop doesn't see the shared directories on my Win7 machine.

---

### Post by coffeecat on 2009-12-24
> **rumentab said:**
> I'm having the same problem. My Ubuntu on the laptop doesn't see the shared directories on my Win7 machine.

Which version of Ubuntu are you using? Have a look at post #1 in this thread:

[http://ubuntuforums.org/showthread.php?t=1169149](http://ubuntuforums.org/showthread.php?t=1169149)

---

