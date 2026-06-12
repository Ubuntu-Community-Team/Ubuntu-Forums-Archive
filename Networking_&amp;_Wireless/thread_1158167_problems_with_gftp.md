---
title: "problems with gftp"
date: 2009-05-13
forum: Networking &amp; Wireless
---

### Post by 22stefano on 2009-05-13
I recently installed UBUNTU jaunty jackalope and I found a problem when uploading my 
web pages:
I created a folder into desktop called "www.steffondatabase.com" (that is not the name of my website). In this folder, I created another folder "images".
In the [www.steffondatabase.com]("http://www.steffondatabase.com") folder, i put all my pages.
When i use gftp and I upload the folder and then i go at users.skynet.be/bk262960/s.htm (s.htm is the name of my homepage) i can see my page but if I click on the link "portale scuola" i have this error:
**Forbidden**

 You don't have permission to access /users.skynet.be/bk262960/&&&/&&&/users/3/web/00/00/38/61/49/&&&/1/&&&/0/&&&/sscuola.html on this server.

How can I solve it?
If i click on "dove sono" i see a withe page and in gftp the size of the file is 0.
Can someone help me? Absolute beginner talk.

---

### Post by kryptikos on 2009-05-13
My suspicion is the folder that has been created on the hosting server does not have the correct permissions. So when you click the link and the webserver attempts to access the location of the htm files it is not allowed. I would check the permission settings on the "images" folder.

---

### Post by 22stefano on 2009-05-14
How can I check (and change if needed) the permission in the "image" folder and why do I need to change the permissions of the images?
In gftp i can see at the right of the image's name "-rw-r--r--"

---

### Post by 22stefano on 2009-05-17
Anyone?

---

