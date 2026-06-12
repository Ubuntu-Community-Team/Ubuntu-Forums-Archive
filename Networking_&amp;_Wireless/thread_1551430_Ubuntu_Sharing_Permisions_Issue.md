---
title: "Ubuntu Sharing Permisions Issue?"
date: 2010-08-12
forum: Networking &amp; Wireless
---

### Post by tsav87 on 2010-08-12
I am able to share folders from my Ubuntu machine to my Windoze machines but there is a slight problem.

You see, I can create a document in the folder from the Windoze side and I can edit it after it has been created, but I am not able to edit it or delete it from the Ubuntu side.  The same is true when I create a document from the Ubuntu side, the Windoze side does not have the permisions to change or delete it...

Help?
TIA

---

### Post by Kerubu on 2010-08-12
In Ubuntu you can change the permissions (of files you create) in Nautilus if you right-click on the file and select 'Permissions'. Allow read-write for 'Others'.

You can do this on the command line with 'chmod' but if you want to do it for files you do not own i.e. ones created in Windows, you'll have to 'sudo chmod'.. or when you save it in windows, change the settings from there but that I don't know how to do

---

