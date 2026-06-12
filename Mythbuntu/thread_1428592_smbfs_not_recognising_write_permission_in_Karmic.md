---
title: "smbfs not recognising write permission in Karmic"
date: 2010-03-13
forum: Mythbuntu
---

### Post by pt123 on 2010-03-13
I was running smbfs fine on Intrepid Mythbuntu but after upgrading to Karmic. I am losing the write permissions on a shared folder located on another computer. 

Note other Computer is running Karmic (Ubuntu - Gnome).

I have tested writing to the share on a laptop running Karmic and it is fine, even on a Mac.

This is the command I am using to mount the share

sudo mount -t smbfs -o username=smbuser,password=thepass //192.168.0.2/Dropbox /media/tricky/Dropbox

Is there something, that has changed?

------

with 8.10 there was a bug with samba and you had to allow it to send the password in plain text.

---

### Post by pt123 on 2010-03-13
adding uid=1000 solves it

---

