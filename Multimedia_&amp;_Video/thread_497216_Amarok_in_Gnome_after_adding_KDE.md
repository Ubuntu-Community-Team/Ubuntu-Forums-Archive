---
title: "Amarok in Gnome after adding KDE"
date: 2007-07-10
forum: Multimedia &amp; Video
---

### Post by Scotty1982 on 2007-07-10
I dono if many people out there use Gnome and KDE, i like to have both installed, 'cuz i like certain aspects of both. however as nice as it is to have both, it seems to make Amarok have a issue, here's the problem:

After adding KDE, if you open Amarok in KDE it'll no longer open properly in Gnome.

Solution:

open up the session manager in Gnome (System - Preferences - Sessions), and add kdeinit so it starts when Gnome starts. After that, either start it manually for your current session (open up a terminal and enter kdeinit) or log out and log back in.

Now, Amarok will once again run in Gnome.

[COLOR="Red"]WARNING:: I don't know enough about linux to know if there are any issues that this will cause, i'm a absolute noob in linux, but it seems to work fine for me.[/COLOR]

also, for other noob's out there, if you want a app to autostart when you log in, just add it to the list in the session manager, and it'll load when you log in. kinda a sweet feature, that's what i use to launch beryl-manager automatically so i get the effects and theme i like right off.

---

