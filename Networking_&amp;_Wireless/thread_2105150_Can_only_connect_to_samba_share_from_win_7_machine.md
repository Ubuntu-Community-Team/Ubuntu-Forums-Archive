---
title: "Can only connect to samba share from win 7 machine using IP address and not hostname"
date: 2013-01-15
forum: Networking &amp; Wireless
---

### Post by sizo4 on 2013-01-15
Hi,

I am a beginner when it comes to Linux, and have recently put together a media server, holding all my movies, running ubuntu 12.04.

After following tutorials and forums i can successfully ping, by hostname and ip, my windows desktop box and my media server ubuntu box fine, and vice versa.

I have configured samba to set up a share called Movies on my media server. I have set up an account on samba using my linux username, windows username with my linux password.

My ubuntu box is now visible on my network tree on my win7 box, as is the Movies share. however when i try to access the Movies share from the win7 box i do not have permission to do so.

i have noticed that by using the static ip address i issued my ubuntu media server, i can access the share with ease.

However i would like to be able to resolve the issue and access the share using the hostname of my ubuntu meda server box.

Sorry if i am a bit unclear in my set up!

Thanks

---

### Post by sizo4 on 2013-01-15
Managed to solve the issue with the following:

in /etc/samba/smb.conf file, after the WORKGROUP line, added the following:

netbios name = PC_NAME
Where PC_NAME is the name of my PC

Then resarted the samba service sudo service smbd restart

---

