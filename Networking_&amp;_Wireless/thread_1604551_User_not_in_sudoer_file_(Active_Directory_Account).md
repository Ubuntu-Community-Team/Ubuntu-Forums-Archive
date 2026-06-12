---
title: "User not in sudoer file (Active Directory Account)"
date: 2010-10-24
forum: Networking &amp; Wireless
---

### Post by ace0022 on 2010-10-24
Trying my luck in this forum since I have not gotten an answer...

Hi all,

I have been trying to add my ubuntu 10.04 to my Windows 2008 Server R2  Active Directory to access my shares and files.  I have managed so far  to add it the machine to Active Directory with LikeWise-Open but when I  try to access any share, ubuntu says cannot retrieve shares from windows  network.  So I found this [https://help.ubuntu.com/community/Mo...resPermanently]("https://help.ubuntu.com/community/MountWindowsSharesPermanently")  and ran into a different problem.  When I try to sudo anything I get " user not in sudoer file".  I have tried to add my active directory user  name into the sudoer file by adding domainname\username to both the  admin and the sudo sections but once I log in to the ubuntu with my  active directory account, I still can't access the sudo feature.

Any help guys would be awesome!

---

### Post by ace0022 on 2010-10-24
Solved my own problem after some trial and error...  Hope this helps someone else..

(This is assuming you already have it joined to AD, if not use this link [http://www.likewise.com/resources/documentation_library/manuals/open/likewise-open-54-guide.html#id2993474](http://www.likewise.com/resources/documentation_library/manuals/open/likewise-open-54-guide.html#id2993474))

To add an Active Directory to a sudoers file do the following:

First log in "local" to the ubuntu workstation.

Open a terminal and type "sudo -i"

Enter Password

Type "visudo"

Go to where it says "%sudo" right under it make a space and type "%domainname\\activedirectoryOU ALL=(ALL) ALL"

Once done click "CTRL+X" to save changes.

When it confirms, clear the ".tmp" from the end of the save file.

Now log in with your domain credentials and launch a terminal to test it.

---

### Post by baodad on 2011-05-05
Thanks for posting your solution.  I'm trying to do the same thing, but I don't want ALL of my AD users to be able to sudo, just a few.  How would I do this?

I'll post if I find a solution.

---

### Post by eentonig on 2011-05-05
Put the AD users in a seperate OU and configure that?

---

### Post by baodad on 2011-05-05
I have a hard time with the term "OU".  I don't fully understand, but to me that means a Windows AD Group Policy object, and I'd like not to have to create another object in my domain group policy.

My quick fix ended up being (from an account already with root access):
```
adduser MYDOMAIN\username admin
```

This added my AD user to the Ubuntu box's admin group in /etc/group.  After that when I logged in as MYDOMAIN\username I could sudo -i to root.

FWIW, for MYDOMAIN I used my domain's short NetBIOS name.

What I really want to do is add my AD domain's Administrators group as sudoers.  But for now this will work.

---

### Post by baodad on 2011-05-05
Here's the answer!

[http://www.youtube.com/watch?v=1X1DZbpCKQA](http://www.youtube.com/watch?v=1X1DZbpCKQA)

---

### Post by ericpeac0ck79 on 2012-04-26
> **ace0022 said:**
> Solved my own problem after some trial and error...  Hope this helps someone else..

(This is assuming you already have it joined to AD, if not use this link [http://www.likewise.com/resources/documentation_library/manuals/open/likewise-open-54-guide.html#id2993474](http://www.likewise.com/resources/documentation_library/manuals/open/likewise-open-54-guide.html#id2993474))

To add an Active Directory to a sudoers file do the following:

First log in "local" to the ubuntu workstation.

Open a terminal and type "sudo -i"

Enter Password

Type "visudo"

Go to where it says "%sudo" right under it make a space and type "%domainname\\activedirectoryOU ALL=(ALL) ALL"

Once done click "CTRL+X" to save changes.

When it confirms, clear the ".tmp" from the end of the save file.

Now log in with your domain credentials and launch a terminal to test it.

THANK YOU! :thumbsup:
for all those folks trying to discourage ppl from editing sudoers, i was relieved to find someone to just tell me what I wanted to know!

---

