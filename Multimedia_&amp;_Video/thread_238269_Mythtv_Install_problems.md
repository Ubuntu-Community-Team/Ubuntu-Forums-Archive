---
title: "Mythtv Install problems"
date: 2006-08-17
forum: Multimedia &amp; Video
---

### Post by mattbatt on 2006-08-17
I am trying to install mythtv and when I do the mythtv app creates a mythtv user and installs several files for the mythtv user some in mythtv users home folder.  For some dumb reason it gives read write and execute privilages to user 1002 instead of the mythtv user.  Now the UID (user ID ?) is 1002.  
Question 1: Why is mythtv doing this?
Question 2: is there a way to change files permissions en Masse or by entire folders.  Typing out every file that needs to be changed in terminal isn't an option since I don't know all of the files that are necessary.
Or is there a way to transfer ownership of all of 1002 files to user mythtv.

Thanks.

---

### Post by mattbatt on 2006-08-21
No help from anyone.
Does anyone know how easy Freevo installs on ubuntu?

---

### Post by crispy_420 on 2006-08-22
It install pretty easily. I believe it is the repos but does it work as well as mythtv. Like you and many others, mythtv install attempts have failed after several attempts. Nothing more frustrating than failing after many hours of work.

But as a side note can you just highlight all files, right click and change permissions. You can do that from a root window.

> sudo nautilus 

There will work right?

---

### Post by mattbatt on 2006-08-25
well I tried that I could change many of the properties for a selection but not permissions.
many hours try days.
but I can't complain too much there is a disclaimer that this isn't for the noobie lik me.

---

