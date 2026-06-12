---
title: "NT_STATUS_LOGON_FAILURE with smbclient and scheduler"
date: 2009-08-21
forum: Networking &amp; Wireless
---

### Post by FlintZA on 2009-08-21
Hi, 
I'm trying to set up a chron job with scheduler to certain files up to a windows share. I have the following in /home/Backups/copybackups:
```

smbclient '\\MyServer\MyShare' -U 'myuser%mypass' -c 'lcd /home/Backups;prompt;mput test*'

```

When I run this in the terminal as follows it works perfectly: 
```
sudo /home/Backups/copybackups
```

However when I add a task to scheduler as root, and set it's command to /home/Backups/copybackups and run the task to test it, I get the following output:
```
session setup failed: NT_STATUS_LOGON_FAILURE
Press ENTER to continue and close this window.
```

Can anyone suggest what I might be doing wrong?

---

### Post by dmizer on 2009-08-21
Perhaps the 6th link in my sig will help. While what you're doing isn't strictly samba browsing, I would suggest the same fixes for the NT_STATUS_LOGON_FAILURE error.

---

### Post by FlintZA on 2009-08-21
> **dmizer said:**
> Perhaps the 6th link in my sig will help. While what you're doing isn't strictly samba browsing, I would suggest the same fixes for the NT_STATUS_LOGON_FAILURE error.
Thanks dmizer. I'm trying to avoid having to go through mounting, copying and then unmounting (and I really don't want to leave the share mounted for security reasons), but if I end up having no choice I'll dive into your tuts (looked at #6 and #2 briefly) and do he mount/unmount.

---

### Post by dmizer on 2009-08-21
> **FlintZA said:**
> Thanks dmizer. I'm trying to avoid having to go through mounting, copying and then unmounting (and I really don't want to leave the share mounted for security reasons), but if I end up having no choice I'll dive into your tuts (looked at #6 and #2 briefly) and do he mount/unmount.

Link #6 doesn't have anything to do with mounting (which is why I suggested it), let me know if it works for you.

---

### Post by FlintZA on 2009-08-21
> **dmizer said:**
> Link #6 doesn't have anything to do with mounting (which is why I suggested it), let me know if it works for you.
Link 6 and it's subtopics deal with enabling smb browsing, which works in my case. Actually using smbclient works as well-when not used from chron, perhaps I missed what's applicable in your link to this case? :)

---

### Post by dmizer on 2009-08-21
Does it work with smbclient if you use the IP address of the server instead of the server name?

---

### Post by FlintZA on 2009-08-21
Nope, same thing.. It runs fine under the terminal with sudo, but as a root chron job it fails :(

---

