---
title: "Apache download file through symlink"
date: 2013-08-05
forum: Networking &amp; Wireless
---

### Post by dannyvanderzande on 2013-08-05
I have a apache server at my ubuntu 13.04 server which I mainly use to send files to family and friends or store a few files I need a lot when I'm not home.
My problem is that I would like to put symlinks in my /var/www/storage directory to files stored at an other location on the server (for example: /media/downloads/pictures/pictures.rar) so I don't have to copy all files to my root drive which is a pretty small SSD.
Does anyone know how to do this? I already created a few symlinks but it doesn't seem to work. The file I am trying to link has a+rwx rights...
Thanks in advance

---

### Post by SlugSlug on 2013-08-05
Am pretty sure when I used to do this the sub folder and any parent folders all needed permissions set for www-data

---

### Post by dannyvanderzande on 2013-08-05
I believe all files and folders have the right permissions :(

---

### Post by SlugSlug on 2013-08-05
right down to /media ?

---

### Post by dannyvanderzande on 2013-08-05
I think so.. am not sure. Everything is either 777 of 755

---

### Post by SlugSlug on 2013-08-05
is there anything in the logs? /var/log/apache/access.log  or error.log

---

### Post by dannyvanderzande on 2013-08-05
I somehow managed to get it to work although im not sure what I did.. -_-
Thanks for the help anyway.. hehe

---

