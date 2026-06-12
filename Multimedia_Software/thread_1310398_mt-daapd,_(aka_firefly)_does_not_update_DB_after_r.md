---
title: "mt-daapd, (aka firefly) does not update DB after re tagging MP3"
date: 2009-11-01
forum: Multimedia Software
---

### Post by alek66 on 2009-11-01
Im using Mt-daapd, and I corrected some tags of some mp3, but although I went to the webinterface and performed a full re scann, the tags still appear wrong.

is there a way to fix this?

---

### Post by alek66 on 2009-11-03
The problem remains... not only modified tags do not appear modified in the mt-daapd database, even some of the addings do not appear.

I modified  mt-daapd.conf that it is in /etc/ to add my configuration, but the configuration tab on the web interface shows no data.

Can anyone help me?

---

### Post by alek66 on 2009-11-04
I just figure it out! Since I modded mi mt-daapd.conf using VI, it seems that webinterface, does not recognizes it (i guess)
Cuase, i turned down the module, and started it again, I it did the start song search, and added all of them.

Does anyone knows about this bug?

---

