---
title: "How do I get rid of the gnome panel?"
date: 2011-01-12
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by rubenverweij on 2011-01-12
I want to get rid of the old gnome panel underneath my new one from Unity. I have already removed gnome panel from the /desktop/gnome/session/required_components list via gconf-editor.
However, every time I login, gnome panel gets started anyway.
Could someone please shed some light on this? :)
Thanks!

---

### Post by cariboo on 2011-01-12
Are you logging into the classic desktop, or the ubuntu desktop?

---

### Post by mc4man on 2011-01-12
There was an update to gnome-session today or yesterday that I believe had a temp patch to help with that situation if it was occurring.

Actually almost never happened here, -
If still loading the panel in Desktop login (top-hidden and or bottom), maybe go into ~/compiz/sessions and delete any saved ones.

(haven't been saving any sessions here which I think was helpful in virtually always getting a good unity load.

---

### Post by rubenverweij on 2011-01-13
Thanks for your replies. I was logging in to the "unity desktop", but it seems the update worked for me. If the bugger comes back I'll let you know.

---

