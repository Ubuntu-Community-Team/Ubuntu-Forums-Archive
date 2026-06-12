---
title: "DeVeDe 3.23.0 from repository always seg faults"
date: 2014-08-10
forum: Multimedia Software
---

### Post by spockswhitepants on 2014-08-10
On 14.04 with KDE. 

I can create a project but when I go and try to build it I get this dialog:

[IMG]http://i.imgur.com/hGJvn1l.png[/IMG]

And if I select any thing from that dropdown (which I am guessing then tries to open a file browse dialog) the application blows up. Odd thing is there are file browse dialogs elsewhere in the application that work fine. Any ideas on how to fix?

```
Threads: 1
Creating window /usr/share/devede/wprogress.ui
Creating window /usr/share/devede/wfolder_dialog.ui
Entro en RUN
/usr/lib/devede/devede_convert.py:349: GtkWarning: gtk_tree_model_filter_get_value: assertion 'GTK_TREE_MODEL_FILTER (model)->priv->stamp == iter->stamp' failed
  value=wfolder_dialog.run()
/usr/lib/devede/devede_convert.py:349: Warning: /build/buildd/glib2.0-2.40.0/./gobject/gtype.c:4210: type id '0' is invalid
  value=wfolder_dialog.run()
/usr/lib/devede/devede_convert.py:349: Warning: can't peek value table for type '<invalid>' which is not currently referenced
  value=wfolder_dialog.run()
Segmentation fault

```

---

### Post by mc4man on 2014-08-10
Seems to work ok here in an Ubuntu 14.04 install with an oddity or 2. (like if I choose my home folder to save to it still goes ~/None/movie/movie.iso
Maybe it's a theme issue with the drop down?

You could try to circumvent this if no solution otherwise.
Open ~/.devede
Edit (or add if not there) this line
final_folder:

Ex. here to save .iso to Videos/movie
final_folder:/home/doug/Videos

---

