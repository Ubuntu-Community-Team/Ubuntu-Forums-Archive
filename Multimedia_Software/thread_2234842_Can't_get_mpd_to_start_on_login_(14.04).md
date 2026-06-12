---
title: "Can't get mpd to start on login (14.04)"
date: 2014-07-17
forum: Multimedia Software
---

### Post by doom1le on 2014-07-17
This is my ~/.config/autostart/mpd.desktop

```
[Desktop Entry]
Encoding=UTF-8
Type=Application
Name=Music Player Daemon
Comment=Server for playing audio files
Exec=mpd
StartupNotify=false
Terminal=false
Hidden=false
X-GNOME-Autostart-enabled=false
[ ! -s ~/.mpd/mpd.pid ] && mpd 
```

I've tried without the X-GNOME line and the && mpd line (taken from arch tutorial) without luck. I'm using dwm and my entire music library is located on a samba share. Everything works fine when I manually start mpd after logging in. Any ideas?

---

### Post by mc4man on 2014-07-17
For starters - 
X-GNOME-Autostart-enabled=false
needs to be true

[ ! -s ~/.mpd/mpd.pid ] && mpd
no clue as to purpose & or whether it belongs in a .desktop file

---

### Post by vanadium on 2014-07-18
Probably the .mpd/mpd.pid is there, and thus that very command prevents mpd from starting. Also without this check, mpd by itself may refuse to start if the file is already there. Anyway, this command stands on a line of its own, so I don't think it does anything within the desktop file.

- remove  ~/.mpd/mpd.pid
- Remove the line  [ ! -s ~/.mpd/mpd.pid ] && mpd from your desktop file
- Perform the edit outlined in the previous post
- make sure you are not also starting mpd systemwide. If it is already running systemwide, your local instance will abort because the port it needs is already taken. Note that upon installation using software center, mpd is automatically set up to run system wide). This will eventually disable systemwide startup of mpd (which is setup by default if you install
```

sudo service mpd stop
sudo update-rc.d mpd disable

```

---

