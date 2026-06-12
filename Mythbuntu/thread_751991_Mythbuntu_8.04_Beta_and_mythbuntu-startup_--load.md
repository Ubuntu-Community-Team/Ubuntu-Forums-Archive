---
title: "Mythbuntu 8.04 Beta and mythbuntu-startup --load"
date: 2008-04-11
forum: Mythbuntu
---

### Post by toniivars on 2008-04-11
Hello,

Recently I've installed Mythbuntu 8.04 beta on my HTPC, then, each time I boot I get a sudo window to execute: 

> mythbuntu-startup --load

Then, nothing is happen, and mythfrontend isn't started automatically.


If I execute the command on a prompt:

> # sudo mythbuntu-startup --load

I get the following warnings and errors:

> 
/usr/bin/mythbuntu-startup:59: GtkWarning: Failed to set text from markup due to error parsing markup: Error on line 1: Character ' ' is not valid at the start of an entity name; the & character begins an entity; if this ampersand isn't supposed to be an entity, escape it as &amp;
  self.glade = gtk.glade.XML(PATH + '/mythbuntu_live_autostart.glade')
/usr/bin/mythbuntu-startup:59: GtkWarning: gtk_tree_row_reference_new: assertion `GTK_IS_TREE_MODEL (model)' failed
  self.glade = gtk.glade.XML(PATH + '/mythbuntu_live_autostart.glade')
/usr/bin/mythbuntu-startup:59: GtkWarning: gtk_cell_view_set_displayed_row: assertion `GTK_IS_TREE_MODEL (cell_view->priv->model)' failed
  self.glade = gtk.glade.XML(PATH + '/mythbuntu_live_autostart.glade')
/usr/bin/mythbuntu-startup:59: GtkWarning: Failed to set text from markup due to error parsing markup: Error on line 1: Character ' ' is not valid at the start of an entity name; the & character begins an entity; if this ampersand isn't supposed to be an entity, escape it as &amp;
  self.glade = gtk.glade.XML(PATH + '/mythbuntu_live_autostart.glade')
/usr/bin/mythbuntu-startup:59: GtkWarning: gtk_tree_row_reference_new: assertion `GTK_IS_TREE_MODEL (model)' failed
  self.glade = gtk.glade.XML(PATH + '/mythbuntu_live_autostart.glade')
/usr/bin/mythbuntu-startup:59: GtkWarning: gtk_cell_view_set_displayed_row: assertion `GTK_IS_TREE_MODEL (cell_view->priv->model)' failed
  self.glade = gtk.glade.XML(PATH + '/mythbuntu_live_autostart.glade')



How can I fix this issue?


Thanks!

---

### Post by jouzts on 2008-04-11
Same problem here. Recent install and more recent update. I notice also that gtk-jockey is crashing on the way to trying "sudo mythbuntu-startup --load"

---

### Post by laga on 2008-04-11
For some reason, you have mythbuntu-live-autostart installed. Remove that package and file a bug report at [https://bugs.launchpad.net/mythbuntu](https://bugs.launchpad.net/mythbuntu)

---

### Post by superm1 on 2008-04-11
If you have it installed, that means that the installer crashed trying to activate VNC (known issue on the beta).  Please reinstall without activating VNC because you will likely have other issues that you run into...

---

### Post by kacheng on 2008-09-23
I am still seeing this error on Mythbuntu 8.10 Alpha 6.

---

### Post by superm1 on 2008-09-23
> **kacheng said:**
> I am still seeing this error on Mythbuntu 8.10 Alpha 6.
Remove the package mythbuntu-live-autostart

---

### Post by kacheng on 2008-09-24
Thanks, but I already took your advice to reinstall without activating VNC to avoid future issues.
:)

---

