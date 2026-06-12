---
title: "How to setup network with Dual boot XP/Dapper Desktop and Dapper Laptop"
date: 2006-07-02
forum: Networking &amp; Wireless
---

### Post by newlinux on 2006-07-02
Hello everyone,

I currently have a dual-boot WinXP and Dapper Desktop at home. In a couple weeks I'll have a laptop with only Dapper on it. I want to be able to share files and printers between the two computers, regardless of which OS the desktop has booted to (mostly media and some application files).

Info:

   [LIST]
[*] All printers are physically connected to the desktop and I can print to all printers from either OS currently
[*] The laptop will connect to the network wirelessly most of the time; My network is cable modem to router (w/wireless and physical connections) to computers...
[*] The files from my XP NTFS share are already visible when I boot dapper.
[*] I will probably be booting Dapper most of the time on the desktop, if this is any consideration for tradeoffs
[*] I also have a work laptop (WinXP) that may occasionally connect to the network.
[/LIST]


What's the best way to go about setting this up? Samba? SSH? NFS? Some combination?

I'm pretty new to all this and your help is greatly appreciated.

---

### Post by woedend on 2006-07-02
samba gets my vote.  search the forums from samba...its all here somewhere.

---

### Post by newlinux on 2006-07-03
Thanks for the advice. From what I've read, I think I'll actually just need to install smbfs on my laptop (running Dapper) to access my Windows shares and printers when my desktop is booted in XP, and since all I will want to do from my work laptop (XP) is use the printers, I should be able to setup CUPS to print when my desktop is booted Dapper. And when my Desktop is booted Dapper, my Dapper laptop shouldn't have any problems accessing files or printers. That sound right?

---

### Post by tturrisi on 2006-07-03
[http://ubuntuguide.org/wiki/Dapper#Networking](http://ubuntuguide.org/wiki/Dapper#Networking)

---

### Post by newlinux on 2006-07-17
I ended up going with Samba for everything. works fine. Thanks!

---

