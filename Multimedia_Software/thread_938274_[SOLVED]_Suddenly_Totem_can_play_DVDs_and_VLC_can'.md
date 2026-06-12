---
title: "[SOLVED] Suddenly Totem can play DVDs and VLC can't!"
date: 2008-10-04
forum: Multimedia Software
---

### Post by rainwalker on 2008-10-04
I'm on Hardy (8.04) and I've noticed that suddenly VLC's playback is scrambled (video and sound), yet Totem plays them perfectly. This wasn't the case a month or two ago, but I have no idea what I did to change things. I really don't care that much as long as DVDs play, but I like VLC and it bugs me that it suddenly stopped working.

Any idea what could have happened?

---

### Post by mc4man on 2008-10-04
If you were to open vlc from the terminal and then go file -> open disc, what shows up in the terminal?

---

### Post by rainwalker on 2008-10-04
Actually I just noticed that this only happens when the movie auto-plays right when I put it in; If I open VLC and select the disk to play it works...:?

---

### Post by mc4man on 2008-10-04
right click on applications -> edit menus, highlight sound and video and on the left side right click on vlc -> properties. Change the command to either vlc %f or vlc %m  (just remove the U and enter f or m

---

### Post by rainwalker on 2008-10-04
> **mc4man said:**
> right click on applications -> edit menus, highlight sound and video and on the left side right click on vlc -> properties. Change the command to either vlc %f or vlc %m  (just remove the U and enter f or m

That worked! What are those %f, %m and %u operators for?

---

### Post by mc4man on 2008-10-04
> What are those %f, %m and %u operators for

this is a general description (about 2/3 of the page down

[http://standards.freedesktop.org/desktop-entry-spec/desktop-entry-spec-1.0.html](http://standards.freedesktop.org/desktop-entry-spec/desktop-entry-spec-1.0.html)

%U never has been any good to autoplay vlc
%m means 'mini icon' (got me there) it's not used anymore but still works fine ( used to use it in gutsy to set vlc to auto play (%d isn't used either but also has it's uses

---

### Post by rainwalker on 2008-10-04
> **mc4man said:**
> this is a general description (about 2/3 of the page down

[http://standards.freedesktop.org/desktop-entry-spec/desktop-entry-spec-1.0.html](http://standards.freedesktop.org/desktop-entry-spec/desktop-entry-spec-1.0.html)

%U never has been any good to autoplay vlc
%m means 'mini icon' (got me there) it's not used anymore but still works fine ( used to use it in gutsy to set vlc to auto play (%d isn't used either but also has it's uses

Cool, thanks :)

---

