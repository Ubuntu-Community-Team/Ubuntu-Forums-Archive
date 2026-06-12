---
title: "feh cycle-once but do not terminate"
date: 2012-09-28
forum: Multimedia Software
---

### Post by dremelts on 2012-09-28
I am using feh (version 2.2) to display a slideshow.  I have a script that first starts audacious with an mp3 file for the music and then forks feh with these options:
 -F -Y --cycle-once -D 2 -f <filelist>

If I don't use --cycle-once it keeps looping thru the filelist.  When I do use --cycle-once feh abruptly terminates after the last slide. Visually, I find this very startling. I would like to be able to tell it to pause on the last slide but I don't see a command line option to do this.

To get around this I just have the script call feh again with these options:
  -F -Y <lastslide.jpg>

This is much less jarring but there is still a hiccup or stutter as one session of feh ends and the next one starts.

Does anyone know how I can get feh to pause on the last slide?

(Also, transitions would be nice ;) )

Dave

---

