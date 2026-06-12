---
title: "Can't connect from Windows to share"
date: 2006-06-28
forum: Networking &amp; Wireless
---

### Post by dickosoft on 2006-06-28
Hello,

I have setup a network share in ubuntu. My smb.conf says the following:

> [httpdocs]
comment = webdata
path = /var/www/
available = yes
browseable = yes
public = yes
writable = yes
create mask = 0777
directory mask = 0777
force user = nobody
force group = nogroup

From my other ubuntu machine I can connect. But from my windows machine I see the computer in the workgroup, but when I connect it requires username and password. When I fill in my username and password from the machine, it can't connect!

Can somebody help me with this annoying problem? Thanks in advance

---

### Post by Footer on 2006-06-29
On the Ubuntu machine where you're sharing the files from, did you:

sudo smbpasswd -a username

?

Sounds like you need to set the username/password on the Ubuntu box before the Windows box will be able to connect to the share.

:)

---

