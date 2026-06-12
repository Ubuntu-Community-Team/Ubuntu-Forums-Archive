---
title: "Evince Configuration Files"
date: 2014-09-15
forum: Multimedia Software
---

### Post by actionmystique on 2014-09-15
**_Environment_: Ubuntu 14.04 - Evince 3.10.3**

Hello guys,

I've been using Evince as a PDF viewer for quite some time. The cool thing is that it remembers the last viewed page in all read PDF documents.

I've tried to compile and install a new version (3.12.1). Alas, all this memory has been lost in the process. 
Does anyone know which file(s) contain(s) this information so that it can be restored from a backup?

---

### Post by slickymaster on 2014-09-15
You might try ```
$HOME/.local/share/gvfs-metadata/
``` which is where evince bookmarks are stored as GIO metadata.

---

### Post by actionmystique on 2014-09-15
Thanks for your answer.

When I compare this folder as it exists today with the same directory as it was before I installed the new Evince version, only the following files have been changed:

- root-xxxx.log
- root
- home-yyyyy.log
- home

If we dismiss the log files (which are unreadable btw), which one should be restored?

---

### Post by slickymaster on 2014-09-15
Those log files are the GIO metadata where Evince saves the bookmarks.

---

### Post by actionmystique on 2014-09-16
Restoring all 4 files did the trick.
Thanks for your help.

However, I think it's time to evaluate another PDF reader, such as Okular.

---

### Post by peterzay on 2015-02-22
When I monitor /gvfs-metadata during evince use while bookmarking, only the 2 home files change.  The 2 root files do not.  When I transport those 2 home files to another identical Ubuntu installation, the bookmarks are lost.

By the way, other processes unrelated to evince also write into those 2 home files.  This makes them of questionable use to backup evince bookmarks.

Is there a Firefox style dedicated bookmark file that evince can use?  Perhaps a compile time option might exist, or be made to exist.  Developers, are you listening?

---

### Post by slickymaster on 2015-02-23
> **peterzay said:**
> <...snip...>Developers, are you listening?
I would advise you to report it upstream: [https://bugzilla.gnome.org/](https://bugzilla.gnome.org/)

---

