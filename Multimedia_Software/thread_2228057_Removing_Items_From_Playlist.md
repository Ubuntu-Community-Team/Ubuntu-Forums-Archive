---
title: "Removing Items From Playlist"
date: 2014-06-05
forum: Multimedia Software
---

### Post by Stob on 2014-06-05
When I open Movie Player, click "Movies", all the recently played videos are shown. How can I clear this list?

---

### Post by mc4man on 2014-06-05
> **Stob said:**
> When I open Movie Player, click "Movies", all the recently played videos are shown. How can I clear this list?

Well it's not a playlist, it's from 'recently used'.  The last 5 entries are drawn from ~/.local/share/recently-used.xbel though that file is not exclusive to Totem.
Easiest is just to delete the file & lose all the recently used entries for all apps that use that file, or open in a text editor, search for "Totem" & remove the complete entry(s) for just totem. 
(from <bookmark href=..... to   </bookmark> per entry
I don't believe totem has any option to not create/save recently used.

---

