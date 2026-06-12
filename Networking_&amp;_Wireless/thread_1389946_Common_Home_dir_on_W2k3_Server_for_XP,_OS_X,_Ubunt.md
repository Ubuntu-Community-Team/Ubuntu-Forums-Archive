---
title: "Common Home dir on W2k3 Server for XP, OS X, Ubuntu"
date: 2010-01-25
forum: Networking &amp; Wireless
---

### Post by kmaynard on 2010-01-25
Our school originally had a Windows NT4 Server, and about 30 NT4 Workstations using MS software. I am trying to liberalise things a bit. We now have 100 Workstations running XP and OS X in a Windows 2003 domain. Thunderbird, Firefox and OpenOffice form the common thread. Users on either system have a common home directory on the server. I should like to add Ubuntu workstations to the mix. The goal is to allow any user to log on to any workstation regardless of OS, and have access to their own files.

I have added Unix support in the W2K3 servers, installed LDAP, Samba, Winbind to Ubuntu, and managed to get Ubuntu to join the domain, and for users to authenticate via LDAP to the domain.

I need advice on how to assign a user's Ubuntu home directory to be on the server. If I do a 'getent' I can see that the location specified in AD makes its way to Ubuntu, but I don't know how to get this mounted. So far, my best effort has been to mount the users' share //SERVER/Users with an entry in fstab, specifying /media/users as the mount point. This, I understand, should mount when Ubuntu boots. In AD, I specify /media/users/username as the Unix home dir. When my new user logs in, it creates the home dir on the windows share, and .bash_logout, .bashc, .profile, examples.desktop, then crashes saying 'could not update ICEauthority file' (encouragingly, it IS trying to create it in the expected place). Also, Nautilus raises a similar objection. I have set windows file protections to Everyone, full access, to see if that is the problem, but to no avail. I have made the Ubuntu wkstn a member of UnixUsers which has full access, in a further attempt to grant access.

Maybe I should let Ubuntu create a local home directory, and automatically (somehow) put a shortcut to the real home directory on the server in it?

---

### Post by de Silentio on 2010-05-12
Hello kmaynard, wondering if you had any luck.  I have the exact same problem.
 
Thanks,
John

---

