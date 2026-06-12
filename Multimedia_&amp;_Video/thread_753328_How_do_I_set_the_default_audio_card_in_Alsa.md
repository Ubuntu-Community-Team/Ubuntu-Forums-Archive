---
title: "How do I set the default audio card in Alsa?"
date: 2008-04-12
forum: Multimedia &amp; Video
---

### Post by phinn on 2008-04-12
The way I set my default card (although there should be an easy GUI way but I don't think the one in System->Pref->Sound actually works)

is:   asoundconf set-default-card [card name]

you can get the card name from doing:  asoundconf list

Hope that helps.

edit: this was edited because I figured it out and cannot delete this thread

---

