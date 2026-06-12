---
title: "Um, where's the UbuntuStudio apps?"
date: 2008-01-20
forum: Multimedia Production
---

### Post by flowbot on 2008-01-20
I've freshly re-installed Gutsy, and wanted to get audio apps going again - however, there are no Ubuntu Studio applications in Synaptic ... I thought all the Ubuntu Studio apps were in the main repos? Where can i get them?!

---

### Post by logos34 on 2008-01-21
Do youhave universe repo enabled?

> $ apt-cache search ubuntustudio
ubuntustudio-audio - Ubuntu Studio Audio Package
ubuntustudio-audio-plugins - Ubuntu Studio audio plugins Package
ubuntustudio-default-settings - Default settings and artwork for the UbuntuStudio desktop
ubuntustudio-desktop - Ubuntu Studio Desktop Package
ubuntustudio-gdm-theme - Ubuntu Studio - GDM theme
ubuntustudio-graphics - Ubuntu Studio graphics Package
ubuntustudio-icon-theme - UbuntuStudio Icon theme
ubuntustudio-look - Ubuntu Studio look
ubuntustudio-menu - Menu for Ubuntu Studio
ubuntustudio-screensaver - UbuntuStudio screensaver
ubuntustudio-sounds - Ubuntu Studio's GNOME audio theme
ubuntustudio-theme - Ubuntu Studio look - GTK and Metacity theme
ubuntustudio-video - Ubuntu Studio video Package
ubuntustudio-wallpapers - Ubuntu Studio - Wallpapers
ubuntustudiolauncher - Music applications launcher
usplash-theme-ubuntustudio - Usplash theme for Ubuntu Studio

 the ubuntustudio-dekstop is a metapackge.  -audio appears to be what you're looking for

---

### Post by flowbot on 2008-01-21
According to Synaptic, I've got Universe Repo enabled:

[IMG]http://i188.photobucket.com/albums/z30/gnuworld/screenshots/Screenshot-2.png[/IMG]

The only ubuntustudio package that turns up in Synaptic search is *usplash-theme-ubuntustudio*.

---

### Post by logos34 on 2008-01-21
maybe there's something here that will solve your problem:
[https://help.ubuntu.com/community/UbuntuStudio](https://help.ubuntu.com/community/UbuntuStudio)

---

### Post by flowbot on 2008-01-21
is cool - i found a thread with someone's default sources.list, and that has worked ... don't know what was wrong with mine, as they seemed pretty similar. thanx anyway.

---

