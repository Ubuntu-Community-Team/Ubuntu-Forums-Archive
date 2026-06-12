---
title: "VLC - Ubuntu 17.04 &amp; VLC Launch on Startup"
date: 2017-09-21
forum: Multimedia Software
---

### Post by licketylips on 2017-09-21
[COLOR=#111111][FONT=Ubuntu]I've just installed the latest version of VLC on Ubuntu 17.04 & I've set it to launch automatically using Ubuntu Startup Applications, however its not working. Is anyone else having the same issue or know how to fix/tell me what [/FONT][/COLOR][COLOR=#111111][FONT=Ubuntu]I'm doing wrong? VLC works OK when manually selecting icon or via the dash
[/FONT][/COLOR][COLOR=#111111][FONT=Ubuntu] .[/FONT][/COLOR][IMG]https://i.stack.imgur.com/UREyV.png[/IMG]

---

### Post by howefield on 2017-09-21
Try changing the command to launch VLC to 

```
/usr/bin/vlc
```

---

### Post by licketylips on 2017-09-21
Yes, I've also tried /usr/bin/vlc - it didnt work either.

---

### Post by howefield on 2017-09-21
Working for me with the following contents in the vlc.desktop file. (Caveat : I'm using 17.10)

```
[Desktop Entry]
Name=VLC
GenericName=Video PLayer
Exec=/usr/bin/vlc
Terminal=false
Icon=vlc
Categories=Video
Type=Application
StartupNotify=false
X-GNOME-Autostart-enabled=true
```

View the file with gedit or nano, how does it compare to the above ?

```
nano ~/.config/autostart/vlc.desktop
```

---

### Post by licketylips on 2017-09-21
Here's whats in my vlc.desktop :

[Desktop Entry]
Type=Application
Exec=/usr/bin/vlc
Hidden=false
NoDisplay=false
X-GNOME-Autostart-enabled=true
Name[en_AU]=vlc
Name=vlc
Comment[en_AU]=
Comment=

---

### Post by howefield on 2017-10-04
Take a back up of the .desktop file and change it to replicate what I wrote in post #4.

Does it work with that ? If not then just revert the .desktop file back to what it was.

---

### Post by mc4man on 2017-10-04
An outside possibility is you installed the snap version of vlc which is not launched from /usr/bin & may not launch from terminal with just vlc.
To check run /usr/bin/vlc from a terminal

---

