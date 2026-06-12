---
title: "Permissions"
date: 2009-06-08
forum: Mythbuntu
---

### Post by uncle hammy on 2009-06-08
I seem to be chasing my tail on this one and am hoping someone can help.  I have a directory on my backend /media_storage ownership is mythtv:mythtv, permissions are drwsrwsrwx.  I mount one of drives to this folder with XFS, and it is shared with samba.  I want this folder to be completely public to anyone on my network, including a couple windows machines.

The problem I am having is with new files or folders created in the directory.  I want them to be created with ugo+rwx, however then are being created with u+rwx,g+rx,o+rx with a group ownership of mythtv and user ownership of the user that created the directory.  So for example, if I add a folder from my windows machine, the ownership will be nobody:mythtv.  I can do anything with this folder from windows, but if I go to the linux machine itself I have to chmod the folder to add permissions before I can even add a file into the new directory.

I have been googling for hours and have tried umask, chmod, chown, a couple "x"acl commands and I can't seem to come up with anything.

Is there a plain and simple way to make this folder open to everyone, and have anything added to also be open to everyone?

Thanks

---

### Post by tgm4883 on 2009-06-08
> **uncle hammy said:**
> I seem to be chasing my tail on this one and am hoping someone can help.  I have a directory on my backend /media_storage ownership is mythtv:mythtv, permissions are drwsrwsrwx.  I mount one of drives to this folder with XFS, and it is shared with samba.  I want this folder to be completely public to anyone on my network, including a couple windows machines.

The problem I am having is with new files or folders created in the directory.  I want them to be created with ugo+rwx, however then are being created with u+rwx,g+rx,o+rx with a group ownership of mythtv and user ownership of the user that created the directory.  So for example, if I add a folder from my windows machine, the ownership will be nobody:mythtv.  I can do anything with this folder from windows, but if I go to the linux machine itself I have to chmod the folder to add permissions before I can even add a file into the new directory.

I have been googling for hours and have tried umask, chmod, chown, a couple "x"acl commands and I can't seem to come up with anything.

Is there a plain and simple way to make this folder open to everyone, and have anything added to also be open to everyone?

Thanks

wouldn't a "chown 777 /dir" make it available to anyone?

---

### Post by crez79 on 2009-06-08
maybe a force user or force group or force create mode or force directory mode in your smb.conf. Check the man page for smb.conf. These force the particular parameter to be what you make it in the smb.conf.

---

### Post by uncle hammy on 2009-06-09
> **tgm4883 said:**
> wouldn't a "chown 777 /dir" make it available to anyone?
I am assuming you mean chmod, not chown, and yes it would make it available to anyone.  That's not my issue, my issue is new file/folder created inside the /dir that I've chmod'd...They aren't fully available to anyone they get something more like 722.

---

### Post by uncle hammy on 2009-06-09
> **crez79 said:**
> maybe a force user or force group or force create mode or force directory mode in your smb.conf. Check the man page for smb.conf. These force the particular parameter to be what you make it in the smb.conf.
I will do that and post back on my results, thanks.

---

