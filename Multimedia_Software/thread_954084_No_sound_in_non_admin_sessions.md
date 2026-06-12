---
title: "No sound in non admin sessions"
date: 2008-10-20
forum: Multimedia Software
---

### Post by anakoan on 2008-10-20
Hi, i'm not able to get any sound on non admin sessions. Everything is ok with my main admin user. I took a look to user settings with on an admin session to verify if access to sound devices seems ok and the little box is checked. Anyone knows whats wrong?

---

### Post by markscott on 2009-01-22
I am having the same problems with my 8.10 machine. Any ideas out there? Sound works great for the 2 admin users, but not the other 2 non-admin users. I have made sure they are a part of the "audio" group, and they have been given access permissions to use audio in the user config panel. I am stumped....

thanks
mark

---

### Post by markbuntu on 2009-01-22
Check in System/Administration/Users and Groups that your users are enabled as members of the following groups:
pulse
pulse-access
pulse-rt

---

