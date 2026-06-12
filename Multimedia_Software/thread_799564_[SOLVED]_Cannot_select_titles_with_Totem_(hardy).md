---
title: "[SOLVED] Cannot select titles with Totem (hardy)"
date: 2008-05-19
forum: Multimedia Software
---

### Post by phenest on 2008-05-19
I have a DVD with 2 titles on it. How do I select the 2nd one?

EDIT: If I select title 2 from Totems playlist, it still plays the 1st title even though the title length has changed.

---

### Post by cor2y on 2008-05-19
install totem-xine and then make totem-xine your default media player instead of totem-gstreamer
```
sudo apt-get install totem-xine;sudo update-alternatives --config totem
```
select totem-xine from the list.
Totem-gstreamer and the gstreamer decoders do not have dvd menu navigation yet.

---

### Post by phenest on 2008-05-19
Excellent! That works fine now.

---

### Post by phenest on 2008-05-19
But that does lead me to another question:

Hardy has 2 Totem players/launchers by default. One is marked Gstreamer and the other is not. But, if I recall, they are both Gstreamer. After installing totem-xine, I now have the choice of Xine or Gstreamer. So what was the difference before?

---

