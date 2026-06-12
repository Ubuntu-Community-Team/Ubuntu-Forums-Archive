---
title: "Serpentine fails to write audio CD"
date: 2007-11-10
forum: Multimedia Production
---

### Post by vasiliymeshko on 2007-11-10
When trying to create an audio cd from mp3 files it starts with the progress bar for a few seconds then just closes. When started from commend prompt it displays the following message: 

```
mike@laptop:~$ serpentine
/usr/bin/serpentine:191: GtkWarning: gtk_tree_view_scroll_to_cell: assertion `tree_view->priv->tree != NULL' failed
  gtk.main()

** ERROR **: file mp3-c.c: line 518 (III_huffman_decode): assertion failed: (i <= SSLIMIT * SBLIMIT)
aborting...
Aborted (core dumped)
mike@laptop:~$
```

This is on a system running Ubuntu 7.04. Does anyone know what's going on here?

---

### Post by ashdezign on 2007-11-10
I have had a problem, without the error message. Serpentine appeared to have written the files. They even appeared on the cd when I looked at it, but when i tried to play them they wouldn't play.

---

### Post by vasiliymeshko on 2007-11-11
Anyone?

---

### Post by vasiliymeshko on 2007-11-19
Well, the system in question has been upgraded to 7.10 with a clean install, fixing the issue. I was still wondering what could have been causing that problem.

---

