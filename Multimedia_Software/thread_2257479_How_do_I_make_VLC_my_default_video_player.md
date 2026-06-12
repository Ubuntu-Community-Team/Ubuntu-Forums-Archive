---
title: "How do I make VLC my default video player?"
date: 2014-12-20
forum: Multimedia Software
---

### Post by ktz84 on 2014-12-20
I would like to make VLC my default player for video on 14.10. I can't seem to find anywhere to set the default.

---

### Post by carl4926 on 2014-12-20
settings > then under system > details

---

### Post by ktz84 on 2014-12-20
Thanks carl4926 that was easy. Clearly my googling skills are poor :(

---

### Post by carl4926 on 2014-12-20
> **ktz84 said:**
> Thanks carl4926 that was easy. Clearly my googling skills are poor :(
No worries

---

### Post by mc4man on 2014-12-20
Just to keep in mind in case it comes up - 
Due to a flaw in gnome once you use SS > Details > ... on audio or video it will create a scenario where one will not be able to then change default player for a couple of mimetypes.
The most notable would be .mp4 (video/mp4 is most common by far

In that case to 'free up' either or both if there of these lines in ~/.local/share/applications/mimeapps.list under [Default Applications] would need to be removed - 
video/mp4v-es=
video/x-m4v=

There may be another or so.

---

### Post by ktz84 on 2014-12-20
Thanks mc4man I'll watch out for that when vlc doesn't open when I click a video.

---

