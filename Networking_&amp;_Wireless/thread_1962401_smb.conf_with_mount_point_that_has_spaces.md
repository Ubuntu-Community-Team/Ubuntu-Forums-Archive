---
title: "smb.conf with mount point that has spaces"
date: 2012-04-21
forum: Networking &amp; Wireless
---

### Post by thinktyler on 2012-04-21
I have a mounted external harddrive @ /media/THE GREAT

I typically use CD with single quotes ' ' and it works whenever I'm using terminal.

However,how do I make a correct smb.conf file with the mountpoint?

I have

[Movies]
path = /media/THE\ GREAT/Movies
;     available = yes
; browseable = yes
guest ok = yes
writeable = yes



Any help is greatly appreciated. Whenever I try ls /media/THE\ GREAT/ I get no directory is found. But I know its mounted cause I can access with ls '/media/THE GREAT/Movies'

*EDIT: LS /media/THE\ GREAT/Movies pulls up the directories.

I still get error 2 on xbmc 11.0
Cheers

---

