---
title: "Flickering video"
date: 2008-05-17
forum: Multimedia Software
---

### Post by srikar on 2008-05-17
When i play .mov files , i get a flickering video.

while wid the other video formats theres no problem.


Is there any kinda fix , solution???

I have ati radeon 200 series onboard graphic card.

---

### Post by Gunman1982 on 2008-05-17
Do you use totem to play the video? Do you have compiz activated?
If you use totem and have compiz active then edit the file
~/.gnome2/totem_config
and change the line
video.driver
to
video.driver:xv
and try again

---

### Post by srikar on 2008-05-19
no i dont have compiz activated neither i use totem. I use vlc player.

---

