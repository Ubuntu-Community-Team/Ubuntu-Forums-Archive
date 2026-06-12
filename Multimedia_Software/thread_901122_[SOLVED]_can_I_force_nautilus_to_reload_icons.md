---
title: "[SOLVED] can I force nautilus to reload icons"
date: 2008-08-26
forum: Multimedia Software
---

### Post by fontenot_1031 on 2008-08-26
I have nautilus set to browse with icons and in one folder I had a video that was not quite finished downloading, so when I navigated there nautilus just left the default movie roll icon. Is there a way I can have nautilus rescan the files in the directory so the icon is just a movie still?


I don't mean refreshing the directory, doesn't work

---

### Post by kerry_s on 2008-08-26
maybe try moving it to another folder and back again. :confused:

---

### Post by fontenot_1031 on 2008-08-27
I guess what I'm trying to say is how can I reload these previewable icons? I can get the previews to go away in nautilus with edit > prefrences > preview > other previewable files "never" but then when I put it back to always it doesn't reload any of the other videos, just the clips that finished downloading before I browsed to the folder.

---

### Post by kerry_s on 2008-08-27
> **fontenot_1031 said:**
> I guess what I'm trying to say is how can I reload these previewable icons? I can get the previews to go away in nautilus with edit > prefrences > preview > other previewable files "never" but then when I put it back to always it doesn't reload any of the other videos, just the clips that finished downloading before I browsed to the folder.

i think if it's incomplete, than it might not have a preview.
oh, another thought, try deleting the ~/.thumbnails folder, than it will have to recache everything.

---

### Post by fontenot_1031 on 2008-08-29
> **kerry_s said:**
> i think if it's incomplete, than it might not have a preview.
oh, another thought, try deleting the ~/.thumbnails folder, than it will have to recache everything.

Awesome that works. Thank you. Marked as solved.

---

### Post by adrian.h on 2012-03-15
FYI, you don't have to delete the entire ~/.thumbnails directory, just the failed ones, so just delete the files in  ~/.thumbnails/fail/gnome-thumbnail-factory.  This way, your computer doesn't have to regenerate those images that it has already done.


A

---

