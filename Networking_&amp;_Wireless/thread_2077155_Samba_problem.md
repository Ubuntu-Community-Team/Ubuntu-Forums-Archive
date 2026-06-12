---
title: "Samba problem"
date: 2012-10-27
forum: Networking &amp; Wireless
---

### Post by doublez13 on 2012-10-27
Hey everyone. I've been running a Samba server/domain controller on Ubuntu for years now, and after my 12.10 upgrade last week, I've been running into some issues. I have many shares on my server, and this problem occurs in ALL of them. 
 
Lets say I create an empty word document and do not modify it at all, then I am fine to delete it. If I do any editing to the document, then when I save it, it saves files like "DF4F6H.tmp" along with it. These tmp files cannot be deleted (even when authenicated as root). They can only be deleted from terminal on the Samba Server. Every additional modification gets a new .tmp file added. If you delete the actual word doc from windows, it will appear to be deleted, but when you refresh the window, it will pop back up, and then will say "access denied" when you try to open it. This applies to notpad files and everything. 
 
The only options that I have for my samba shares are...
 
[Share Name]
comment = comment
path = path
read only = no
 
... and these have been working fine for years until my the uprade to 12.10
 
This happens no matter what windows machine I'm on, whether on the Samba Domain or not.
 
When I log into the actual server via terminal and type "ls -al /path/to/share" it shows that the tmp files are owed by the user logged on, so at the least I would think that the user would be able to delete them.
 
I just feel totally stuck on this one. Thanks guys

---

