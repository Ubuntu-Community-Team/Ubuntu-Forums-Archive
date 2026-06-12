---
title: "Difference between Movie Player &amp; Movie Player (GStreamer)"
date: 2008-11-12
forum: Multimedia Software
---

### Post by Dansaycool on 2008-11-12
Hi,

Does anybody know what the difference is between Movie Player and Movie Player (GStreamer) as there both in my applications menu but both seem to do the same thing?

Does the GStreamer one start with different program arguments or something?

Thanks

Dan

---

### Post by mc4man on 2008-11-12
'Movie player' refers to the 'default' totem player, 'Movie Player (GStreamer)' is the gstreamer version specifically.
If you had totem-xine installed you'd see a third entry 'Movie Player (Xine).

In your case (no xine version) they're one and the same.

8.04 and 8.10 allow both to be installed at the same time and one or the other can be set as the 'default totem player'.

sudo update-alternatives --config totem

---

