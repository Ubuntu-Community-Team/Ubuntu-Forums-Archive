---
title: "Muine navagation help"
date: 2010-11-20
forum: Multimedia Software
---

### Post by evworld on 2010-11-20
Can someone tell me how to do this...  Trying to clear watched folders in Muine and don't know how to navigate to the right place.

 You can, however, remove watched folders by editing the /apps/muine/watched_folders GConf string list, and clean out your library by removing ~/.gnome2/muine/songs.db and ~/.gnome2/muine/covers.db.

---

### Post by daneforce on 2010-11-30
A bit late, but:

The watched folders can be found by typing gconf-editor into the run dialog (brought up by Alt+F2) and navigating to the /apps/muine/watched_folders location.

As for cleaning out the library: go to your home folder then press Ctrl+H to display hidden files/folders. The folder /.gnome2/muine should be there. :)

---

