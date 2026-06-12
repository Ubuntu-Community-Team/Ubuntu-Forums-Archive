---
title: "Need help with SAMBA"
date: 2006-01-19
forum: Networking &amp; Wireless
---

### Post by albeano2004 on 2006-01-19
Hey all,
I'm kind of new to linux, but I have given it a go once or twice. I now have a permanent machine to run it on, so I thought I would install Ubuntu 5.10 on it. When I set up SAMBA to share my secondary hard drive (which is mounted in my home folder as "Shared Drive"), it all seems to set up the share ok. However, when I switch over to my windows machine, and try to access my linux box, it asks for a password and username, which I have not specified. :( When I try accessing this through the linux box (which should work, as it doesn't actually have to go through the network, right?), it again asks for this mysterious password/username combination. Please help me! Is there something I need to add to smb.conf? Something I have missed? If you people need any more information, I'd be perfectly happy to oblige.

Cheers,
albeano2004

---

### Post by Quirky on 2006-01-20
I have samba set up for Windows 98 <-> Ubuntu sharing. I had to set up identical users on the Windows 98 machine before anything would work. e.g. user "foobar" exists in Ubuntu, I have to log in as "foobar" (password is not important, it can be the same, or different, it doesn't matter with the default samba settings) on the 98 machine. Then I can see my /home/foobar directory in "My Network". Setting a folder shared in Windows 98 makes it appear in the Network Servers section of Ubuntu.

In the file /etc/sambasmb.conf, I think I altered this section:

[homes]
   comment = Home Directories
   browseable = yes

But I can't remember as it was a while ago I set it all up. I do remeber that I had to fiddle with some settings in Windows too, with associated multiple reboots, I think adding some kind of "Microsoft Network Authentication" as it was dubbed.

---

### Post by jonny on 2006-01-20
Samba users <> Linux users.  This confused me enormously when I was setting up my network.

You need to do one of two things.  Either:

 - enable anonymous access on both client and server.  This is not recommended for security reasons, and I've failed to get it working on Breezy although it worked perfectly on Hoary; or

 - add a separate samba user on the server.  Working from memory, I think it's smbpasswd -u <username> that you need.

---

### Post by jonny on 2006-01-20
[duplicate post removed]

---

