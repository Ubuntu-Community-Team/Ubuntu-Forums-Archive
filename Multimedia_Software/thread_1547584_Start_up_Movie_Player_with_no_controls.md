---
title: "Start up Movie Player with no controls?"
date: 2010-08-06
forum: Multimedia Software
---

### Post by dek8 on 2010-08-06
.


Possible to have the Movie Player launch with the "Show Controls" option off?



thanks

---

### Post by mc4man on 2010-08-07
Pretty easy.
If you want to change the default Totem (Movie Player) then just go in a terminal
```
alacarte
```
Highlight Sound & Video, on the r. side right click on Movie Player -> properties and change the command to 
```
totem --toggle-controls %U
```

If you want to leave the default Movie Player alone and create a 2nd 'instance', then 

```
cp /usr/share/applications/totem.desktop ~/.local/share/applications/totem-noshow.desktop
```

```
gedit ~/.local/share/applications/totem-noshow.desktop

```

When the file opens change the line Exec=totem  %U to the above one.
Edit the line Name=Movie Player to whatever name you wish, then save.
 
The 2nd 'totem' will show up in your Applications menu with name you picked and run without controls

Ex. (name it whatever you wish

> [Desktop Entry]
Name=Movie Player 1
Comment=Play movies and songs
Exec=totem --toggle-controls  %U
Icon=totem
Terminal=false
Type=Application
Categories=GTK;GNOME;AudioVideo;Player;Video;
.......
.......clipped

---

