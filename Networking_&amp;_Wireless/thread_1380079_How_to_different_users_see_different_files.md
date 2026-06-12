---
title: "How to: different users see different files"
date: 2010-01-13
forum: Networking &amp; Wireless
---

### Post by eje211 on 2010-01-13
There's something I would like to do. It's simple, it MUST be possible. I can't find any way to do it by Googling it. I'm must be looking for it in a wrong way.

Let's say I have a directory called dir1. In it, I have these files: A1, A2, A3 belong to user "userA", files B1 and B2 belong to "userB". Both users are in group "groupNO", but the files are in group "groupYES".

What I want is this: if someone tries to mount the folder by NFS (or could it be done with Samba?),[LIST][*] as userA, they can only see (or read) files A1, A2, A3,
[*] as userB, they can only see (or read) files B1 and B2,
[*] as a user in groupYES, they can see and open all the files.
[/LIST]
This is just the principle. If I need to sort them into directories or use another program on the server-side, that's fine with me. I just want the user to just have to mount the folder over the LAN with a user name and password. I'm fairly sure I can do it by SFTP, but, again, I want the client to be able to MOUNT the folder on their local machine over the LAN no to user a special client.

Is that possible? Do I need LDAP? (From what I understand, LDAP is separate from the OS-level mounting process, which is not what I want.)

Thanks to anyone who can help.

---

### Post by chewearn on 2010-01-13
There is no visible/hidden attribute for files; therefore, I don't think what you are proposing is possible.  Instead, you would need to put the files into separate directories for each user.

---

