---
title: "How to setup fileserver files?"
date: 2009-03-12
forum: Networking &amp; Wireless
---

### Post by LIGHTNINJIM on 2009-03-12
I know the title may be misleading but I don't know what else I should call it (SORRY)

I'm currently building a fileserver and am going to use server8.10, connected to 3 ubuntu8.04LTS pc's a DSL laptop and a vista laptop.
My question is; Is it possible to setup the pc's and possibly the laptops to use the fileserver harddrives automatically.

I think what I'm asking is how to setup everything on the network as thin clients (Is this right?) so all of the files are retained on the fileserver

EDIT:- I've tried google and a forum search but I'm not really sure what Im looking for (bet you couldn't tell :)

---

### Post by cariboo on 2009-03-12
Do you just want o connect to the shares automatically on boot?

Jim

---

### Post by Iowan on 2009-03-12
Wikipedia describes thin clients as glorified terminals - all processing done on the server. *Sounds* like you're looking more for an environment where machines do their own processing, but storage is mapped to the server.  NFS can do that for the Linux machines... Samba *might* be the ticket.

---

### Post by LIGHTNINJIM on 2009-03-12
> **cariboo907 said:**
> Do you just want o connect to the shares automatically on boot?

Yes, but I don't know how

---

### Post by LIGHTNINJIM on 2009-03-12
> **Iowan said:**
>  *Sounds* like you're looking more for an environment where machines do their own processing, but storage is mapped to the server.  NFS can do that for the Linux machines... Samba *might* be the ticket.

Are there any tutorials or guides for this?

I've been bashing for a while but still don't know that much.
I have no previous dealings with samba and to be honest even my bashing skills are very limited

---

### Post by Iowan on 2009-03-12
NFS:
[https://help.ubuntu.com/community/SettingUpNFSHowTo]("https://help.ubuntu.com/community/SettingUpNFSHowTo")
[https://help.ubuntu.com/community/NFSv4Howto]("https://help.ubuntu.com/community/NFSv4Howto")

Samba:
[https://help.ubuntu.com/community/SettingUpSamba]("https://help.ubuntu.com/community/SettingUpSamba")
[http://ubuntuforums.org/showthread.php?t=288534]("http://ubuntuforums.org/showthread.php?t=288534")
[http://samba.netfirms.com/]("http://samba.netfirms.com/")

---

### Post by LIGHTNINJIM on 2009-03-12
Thanks so much for the links. you've been a great help.

The last time I posted I recall butttons allowing you to thank people with helpful posts, can't seem to find it now

---

### Post by Iowan on 2009-03-12
The Thanks and [SOLVED] were suspended some time ago when the forum was having stability issues.  Perhaps they'll return, but the help will continue nevertheless.

---

