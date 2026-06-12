---
title: "Weird file sharing issue"
date: 2009-06-08
forum: Networking &amp; Wireless
---

### Post by Leebo on 2009-06-08
Hi all!

I'm having an issue with file sharing every now and again. I have Intrepid running on my desktop and I have a file located in a shared folder that I access regularly from my xp laptop. The file is opened from the network and most of time I can save it back to my linux desktop from the laptop. 

BUT, the problem arises that sometimes after I have the file open, I make changes then go to save it and I get a access violation and tells me I have to save it as a different name, which I am able to save it as a different name via the network on the desktop. No one else is accessing the file and this only happens sporadically. I have to go into my desktop to rename the file back to the original filename.

I was just wondering if anyone would have an idea to why this is.

Thanks

---

### Post by quixote on 2009-06-09
If I understand right, you work on the file in windows, and then save over the network to the shared folder.  Some Windows programs for reasons known only to themselves refuse to save changes to a file unless you give it a new name. 

From the linux side, there is the issue of permissions.  The default permissions are partly closed in linux (not everybody can write to files, only the "owner").  In Windows, they're wide open.  So maybe if you work on the file in linux, it uses the more restrictive permissions.  Then when you want to look at it in windows, it can read it, but it's not allowed to write because the permissions are restricted.

A *no* security way around the problem is to change the permissions on the file in linux to wide open:
```
$ chmod 777 /shared-folder/path/to/filename
``` (or just filename if you're running the command from that folder).  Alternatively, you can right-click the file in nautilus, go to properties, then permissions, and allow "access" "create" and tick "allow execute".

Hope that helps.

---

### Post by theozzlives on 2009-06-09
I don't know if this helps, but when I move a file (or group of files) over SAMBA, it resets the owner to "Nobody" and screwes up my permissions. I just chown & chmod the file(s) and everything's fine.

---

