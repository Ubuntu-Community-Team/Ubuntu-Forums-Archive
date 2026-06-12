---
title: "disallow file or directory deletion on network share"
date: 2009-06-12
forum: Networking &amp; Wireless
---

### Post by dave37 on 2009-06-12
I'm running an Ubuntu Hardy file server for my wife's SOHO.  Now that she had employees, a concern for her is an employee accidentally deleting a file or folder on the shared directory.  They have a directory, let's call it SHARE, that they all must have full read and write access to.  Samba is set up with user level security, and directory and file masks of 0777 as the nature of the business is that they need to write to shared files and directories regularly.

Is there any way to set a permission to disallow file or folder deletion except by the root user (i.e. me, the sysadmin) in order to prevent anyone accidentally deleting data?  And yes, we do have daily off-site backups, but it would be better to prevent the problem than to try and correct it.

Thank you!

---

### Post by bab1 on 2009-06-12
I would look into Linux ACL's.

Start [_**here**_]("http://www.google.com/search?q=linux+acls&btnG=Go!").

---

### Post by dave37 on 2009-06-12
Looks like what I need, without reinventing the wheel, if anyone has any ideas on using the acl to set users Tom, Dick, and Harry so that Tom can delete at will, Dick and Harry cannot, on network share [net share] please advise.

Thanks!

---

### Post by swerdna on 2009-06-13
```
[ShareName]
path = /path_to/shared_directory
read only = no
create mask = 770
force create mode = 770
```
The mask and mode make it so users can read, edit and delete. If you chmod the share with the restricted deletion bit, then only the owner can delete the files. So for admin-only deletion, chown the directory to root:users.

FFI see the share labelled #7 in this tutorial:
[HowTo Configure a Professional File Server on a SOHO LAN]("http://www.swerdna.net.au/linhowtosambaserver.html#rwauth")

Sounds like what you wanted.

---

### Post by dave37 on 2009-06-13
I setup the smb.conf as you noted, and performed sudo chown -R username:groupname /path to directory  and chmod -R 1770 /path to directory 

This restricts deletion of files except by the user named in the chown command, however, users can still delete new files that they create.  Is there a way to also cause newly created files to be non-deletable except by the user named in the chown command? 

Great guide BTW!

Thanks!

---

### Post by swerdna on 2009-06-13
> **dave37 said:**
> I setup the smb.conf as you noted, and performed sudo chown -R username:groupname /path to directory  and chmod -R 1770 /path to directory 

This restricts deletion of files except by the user named in the chown command, however, users can still delete new files that they create.  Is there a way to also cause newly created files to be non-deletable except by the user named in the chown command? 

Great guide BTW!

Thanks!
AFAIK there isn't a way. If they can create a file and edit the file, then they can delete it.

You could create a virtual trash basket that catches all deleted files and then if there's a mistaken deletion, the owner can appeal to the administrator to restore it. See this reference for that sort of thing:
[http://www.google.com/search?hl=en&q=%22vfs+object+%3D+recycle%22&btnG=Search&meta=](http://www.google.com/search?hl=en&q=%22vfs+object+%3D+recycle%22&btnG=Search&meta=)
and this
[http://www.google.com/search?hl=en&q=samba+vfs&aq=f&oq=&aqi=g8g%3As1g1](http://www.google.com/search?hl=en&q=samba+vfs&aq=f&oq=&aqi=g8g%3As1g1)
They should get you started on VFS

---

### Post by dave37 on 2009-06-14
That first link got me all set up, thank you.  Now with a virtual recycle bin the problem is solved!  Thank you very much for your help.

---

