---
title: "Trying to create public shared folder with Samba"
date: 2009-01-16
forum: Networking &amp; Wireless
---

### Post by mishathegoat on 2009-01-16
Hey everyone,

I just installed Ubuntu Server 8.10 on a home made server. I've installed Samba and I'm trying to create a public, writeable folder.

I can see the shared folder fine on my other Ubuntu Desktop machine.. but when I try to create a folder or file from Ubuntu Desktop I get a popup message that says:

[B]"Error while creating directory untitled folder.

There was an error creating the directory in smb://nintendoserver/public%20storage/.

Permission denied"[/B]

Here is my Samba config for the shared folder:
```

[Public Storage]
  path = /home/administrator/public
  public = yes
  writeable = yes
  read only = no
  browsable = yes
  create mode = 0777
  directory mode = 0777
```

---

