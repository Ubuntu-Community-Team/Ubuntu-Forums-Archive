---
title: "Another cifs NAS thread"
date: 2012-07-02
forum: Networking &amp; Wireless
---

### Post by Stardevelop on 2012-07-02
Hi,

I'm completely new to Ubuntu and I want to mount a NAS share.
I've made a directory /media/data and mounted the drive with:

mount -t cifs -o username=video //serveraddress/sharename /media/data

That works! Great!
But when I go to this mountpoint I can see all the folders but i cannot access them..
It says: "The folder contents could not be displayed. You do not have the permissions necessary to view the contents."

Now when I connect to the same share using smb on my macbookpro I can view all the contents.
The folder /media/data is owned by root and i am logged in as system administrator, i'm thinking it has something to do with that..?

I'm running ubuntu 12.04 LTS

---

### Post by Stardevelop on 2012-07-03
Does anybody know how i can access the content in these folders?

---

### Post by Stardevelop on 2012-07-04
Figured it out... I had to use noperm...

mount -t cifs -o rw,noperm,username=video //serveraddress/sharename /media/data

---

