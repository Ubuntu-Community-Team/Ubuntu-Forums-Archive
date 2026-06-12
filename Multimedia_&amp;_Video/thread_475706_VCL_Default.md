---
title: "VCL Default??"
date: 2007-06-16
forum: Multimedia &amp; Video
---

### Post by mschraier on 2007-06-16
How do I make VLC my default player?  Totem opens up and I do not wish to use it

---

### Post by PaulFr on 2007-06-16
Assuming gnome, try the following:

- Find out which file types are being handled by totem currently: **grep totem /usr/share/applications/defaults.list**
- Choose which file types you want vlc to handle (the types that vlc can handle are given by **cat /usr/share/applications/vlc.desktop** at the end of the file)
- Create your version of defaults.list in ~/.local/share/applications/defaults.list - the first line should read [Default Applications] and the lines after that should all be of the form <mimetype>=vlc.desktop. (of course, if you already have a defaults.list in ~/.local/share/applications, you should be adding to it).

For example, if you only want mp4 files to be handled by vlc, your defaults.list should look like

[B][Defaults Applications]
video/mp4=vlc.desktop
[/B]

Logout and login again to get the effect of these changed definitions. If you want all users to get the change, then you are better off changing the system defaults, but I would suggest you try it in your account first, then update /usr/share/applications/defaults.list. Hope this helps.

---

