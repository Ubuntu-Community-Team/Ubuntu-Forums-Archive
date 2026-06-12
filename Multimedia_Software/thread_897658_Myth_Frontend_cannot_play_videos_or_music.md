---
title: "Myth Frontend cannot play videos or music"
date: 2008-08-22
forum: Multimedia Software
---

### Post by lintoon on 2008-08-22
I have a working Myth backend/frontend pc which plays TV, videos, and music fine.

I also have a seperate frontend which can control and watch TV ok.  Unfortunately this frontend machine cannot watch videos (avis mpegs etc) which are stored on my backend pc.
mysql.txt points to my backend IP and has the correct database and username settings.

Samba is set up and working.  For troubleshooting purposes I have set the permissions of the samba shares (Videos and Music) to 777.

Both systems have the same ubuntu username and password.

Any ideas??

---

### Post by lintoon on 2008-08-27
I've sorted it.

I had to mount the video and music directories and point mythfrontend at the mounted directory.

---

