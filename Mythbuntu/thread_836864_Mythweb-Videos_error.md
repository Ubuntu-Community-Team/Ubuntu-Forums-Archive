---
title: "Mythweb-Videos error"
date: 2008-06-21
forum: Mythbuntu
---

### Post by larsolav on 2008-06-21
Good evening,

I just discovered the wonderful world of Mythweb!
Everything works except for the videos .
I created the symlinks as described here:
[http://ubuntuforums.org/showthread.php?t=776014&highlight=mythweb+video](http://ubuntuforums.org/showthread.php?t=776014&highlight=mythweb+video)
And now when I click the video tab, I get a back page with error messages on it like this:
> Error at /usr/share/mythtv/mythweb/objects/Video.php, line 55:
getimagesize(/home/husebo/.mythtv/MythVideo/Cailllou065.jpg) [function.getimagesize]: failed to open stream: Permission denied

Error at /usr/share/mythtv/mythweb/objects/Video.php, line 56:
Division by zero

Error at /usr/share/mythtv/mythweb/objects/Video.php, line 57:
Division by zero

Error at /usr/share/mythtv/mythweb/objects/Video.php, line 55:
getimagesize(/home/husebo/.mythtv/MythVideo/Elmo_ Babies_Dogs_and_More.jpg) [function.getimagesize]: failed to open stream: Permission denied

Error at /usr/share/mythtv/mythweb/objects/Video.php, line 56:
Division by zero

Error at /usr/share/mythtv/mythweb/objects/Video.php, line 57:
Division by zero

Error at /usr/share/mythtv/mythweb/objects/Video.php, line 55:
getimagesize(/home/husebo/.mythtv/MythVideo/Elmo_visits_the_doctor.jpg) [function.getimagesize]: failed to open stream: Permission denied

Error at /usr/share/mythtv/mythweb/objects/Video.php, line 56:
Division by zero
ETC..

Anyone know how to fix this?

Thanks

---

### Post by Go3Team on 2008-09-09
Did you ever resolve this? I'm having the same problem.


Edit:

Fixed the problem.  For some reason the photos uploaded by the mythweb interface had the wrong permissions.

sudo chmod 777 /home/mythtv/.mythtv/MythVideo/picture.jpg

---

### Post by stevanbt on 2008-09-09
Hi,
I run MythWeb and can watch my videos through it - one thing I didn't do was setup the jpegs of the dvds, never got round to it.  By the looks of it you have tried to setup the jpegs of the dvds.  It looks like you have permission problems this is most likely because the user id that runs apache doesn't have access to /home/husebo - that makes sense I think.

You could try to store your dvd jpegs in another location, perhaps try a subdirectory from where your videos are stored.

Hope this helps, Steve.

---

### Post by Weidbrewer on 2008-11-29
I'm having the same problem myself.  I hadn't used MythWeb in a few months...worked totally fine last time I used it.  Not sure what changed.

---

