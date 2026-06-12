---
title: "Disconnecting iPod from Amarok &amp; DVD tray opens!"
date: 2007-06-27
forum: Multimedia &amp; Video
---

### Post by flyingsolo on 2007-06-27
So the title says it all!  I have Amarok & my 8G iPod nano working well together under Feisty but when I click to disconnect the iPod, for some strange reason my DVD tray opens.  Anyone know why? (using an inspiron 6400 bought before Dell started selling them with Ubuntu)

---

### Post by flyingsolo on 2007-06-28
Bump--still curious if anyone has seen this wonky behaviour?

---

### Post by SoCalChris on 2007-06-28
I get the same thing on our computer. It's a homebuilt computer that's about 5 years old. When I disconnect my 80GB ipod through Amarok, my DVD burner tray also opens.

I suspect it has to do with the media device settings.

In the devices tab, click on the Configure Media Device button. There is a setting for "Post disconnect command". Mine by default is set to 'kdeeject -q %d'. I tried removing this command, but Amarok always reverts back to that.

---

