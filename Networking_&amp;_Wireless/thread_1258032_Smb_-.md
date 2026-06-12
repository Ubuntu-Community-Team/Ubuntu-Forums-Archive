---
title: "Smb -"
date: 2009-09-04
forum: Networking &amp; Wireless
---

### Post by nsacco on 2009-09-04
Edit: Crrrrap, I forgot to complete the thread title, sorry. It's supposted to be 'SMB - Ubuntu can access Vista share, but Vista cannot access Ubuntu share'

I've got a strange issue concerning Samba on Ubuntu. I've got a Vista PC, which is my desktop machine. I recently built an HTPC, running Ubuntu Jaunty for XBMC. The problem I'm having is this:

The Ubuntu machine can see my Vista share on the network
The Ubuntu machine can access the Vista share
The Vista machine can see my Ubuntu share on the network
The Vista machine CANNOT access the Ubuntu share

I've read up on this on Google, and I've ruled out two things:

It's not the Vista machine, because my XP laptop has the same exact problem
It's not the router, because I've reset the power on it, and even purchased a new one (I've been needing to replace it anyways)

What confuses me even more is that I CAN get it to work. Here's what I do:

Uninstall 'samba' and it's dependencies
Try to share a folder. This causes Ubuntu to notice that samba isn't installed.
Let Ubuntu install samba, and share the folder

And now it'll work. The Vista machine can access, read, and write on the share. But if I restart, I lose that access. The Vista machine can still see the share after I refresh the Network window, but I get an error: 0x80070035.

I have tried using the share name 'XBMC' and the IP address, neither work. I can ping the IP address of the Ubuntu machine from the Vista machine, but that's yet. Yet, the Ubuntu can still access the Vista share. What possibly could be going on here?

edit: Oh, real quick, just FYI, the Ubuntu and Vista machines use wire network, XP laptop is wireless.

---

