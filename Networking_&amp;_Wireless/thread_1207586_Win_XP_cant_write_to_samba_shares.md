---
title: "Win XP cant write to samba shares"
date: 2009-07-08
forum: Networking &amp; Wireless
---

### Post by greyspoke on 2009-07-08
Hello.  I have been trying various things, and following the advice on a number of forum threads, but I cannot get a Windows XP machine to have read/write access to a share on the Ubuntu machine.  The idea is to for all users to have read/write access to the shared folder.  Here is my smb.conf
> [global]

   workgroup = GOBBY
   server string = %h server (Samba, Ubuntu)
   name resolve order = lmhosts host wins bcast
   security = user
   encrypt passwords = true
   passdb backend = tdbsam
   invalid users = root


[homes]

    guest ok = no
    read only = no

[shared]

    path = /home/shared
    writeable = yes
    public = yes
    read only = No
    create mask = 0775
    directory mask = 0775


The Win XP user is a Samba user and a Unix user on the Ubuntu box, and is a member of the group "sharers" which is the group which has access to /home/shared:
> drwxrwxr-x  3 root    sharers 4096 2009-07-08 13:37 shared
"homes" and "shared" show up as shares on the Ubuntu box in Windows XP.  The "homes" bit works fine with read and write access, and the XP user can see and browse around in the "shared" bit fine.  When the XP user actually logs on to the Ubuntu box under their Unix user name (s)he can access /home/shared and write to it, so if it is a Unix permissions issue it must be a very subtle one.  I have also tried using "force user=" in various ways and that didn't work either, XP insists it has read-only access.

I am now a bit stuck what to try next - any ideas?  Thanks in advance.

---

### Post by greyspoke on 2009-07-08
Belay that, just found the (well, an) answer.  Doh.

Anyhow, the answer lies in the "map read only" option, which I happened upon when scrolling down the smb.conf man page.  I guess that as it was introduced in version 3 it hasn't been included in that many examples that are out there.

The default is "Yes", it needs to be set to "Permissions" if your Unix group permission is going to be recognised.

Like it says [here]("http://us3.samba.org/samba/docs/man/manpages-3/smb.conf.5.html") if you scroll down a way.

---

