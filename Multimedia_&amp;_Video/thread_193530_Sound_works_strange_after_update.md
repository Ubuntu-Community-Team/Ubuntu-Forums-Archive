---
title: "Sound works strange after update"
date: 2006-06-10
forum: Multimedia &amp; Video
---

### Post by Viert on 2006-06-10
Found a strange problem. I installed release version from scratch to my laptop, it worked great and I didn't find any problems. But after autoupdating system sound works only under root priveleges. It means that I hear sound when gdm starts and draws login screen. But after loggin in sound doesn't work at all, the only way to hear something is to start players or smth with sudo.

It looks very strange coz I didn't find any packages updated that could affect sound core...

---

### Post by Viert on 2006-06-10
I found that it was a problem with additional groups for my user, I've lost "audio" group while reconfiguring. Solvation found, thanx.

---

