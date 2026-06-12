---
title: "Rhytmbox doesnt show song notification"
date: 2009-07-24
forum: Multimedia Software
---

### Post by Screatch on 2009-07-24
I would like to see song notification everytime the song is changed, but unfortunately rhythmbox doesn't show me any notification, even through i am sure that "Showing notifications" is enabled. Maybe i am doing something wrong but i never got any song notification and i am pretty sure that this functionality has been implemented.
 I am using Ubuntu 9.04

---

### Post by vinutux on 2009-07-24
no problem for me...........i am using rhythmbox and Banshee....i thik there is no need to enable enything fo this....

---

### Post by xc3RnbFO8P on 2009-07-24
>  gconf-editor
Apps> Rhytmbox> UI> Show_Notification

---

### Post by Screatch on 2009-07-24
> Apps> Rhytmbox> UI> Show_Notification
Told you that checkbox is checked but still no notifications.

---

### Post by xc3RnbFO8P on 2009-07-24
> Told you that checkbox is checked but still no notifications.
Sorry.
Do you album cover in /home/your folder/.cache/rhythmbox/covers
Looks like this bug:
[https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/229197]("https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/229197")

---

### Post by Screatch on 2009-07-24
I do have albums cover, i got no notifications at all, its not like theres no album cover.

---

### Post by Screatch on 2009-07-24
Now there is something i am missing. I found out that Notification works on some songs and dont on others. Sometimes they work and sometimes dont.
For some strange reason, right now they are working.

---

