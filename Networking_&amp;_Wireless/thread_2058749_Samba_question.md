---
title: "Samba question"
date: 2012-09-16
forum: Networking &amp; Wireless
---

### Post by neuman1812 on 2012-09-16
I have two computers running Ubuntu.  Mine and My wifes.

we have the "documents" folder shared out so we can help each other with work.

The problem we run into is,  If I open a document from her //wife/documents share I can only Read-only.  so What I do is save it as a separate name from her origianl... but then she is only able to open that as read-only.

What I think is happening is there is no common permissions between the computers.  So any document I save to her computer , is saved with my computer/user permissions  that dont exist on her's.

I hope this makes sense.  Im sure its and easy fix.  I just cant find it.

---

### Post by Morbius1 on 2012-09-16
There's one easy way out of this:

I don't know what method of Samba you used to create the share - there are 2 - but if you only have the one share you could do this:

Let's say the user name on your system is bob:

Edit smb.conf as root:
```
gksu gedit /etc/samba/smb.conf
```Add the following line to the [global] section right under the workgroup line:
```
force user = bob
```Then restart samba:
```
sudo service smbd restart
```Now let's say your wife's user name is mary. When mary accesses your share mary will be converted to bob. All of the files that bob created will now be accessible to mary. When mary adds a new file it will save with owner = bob. 

Do the exact same thing on mary's machine:
```
force user = mary
```When bob accesses mary's machine he will be converted to mary ....

What you lose in all this is keeping track of who did what you who. Every file on bob's machine will be owned by bob and on mary's machine mary.

---

