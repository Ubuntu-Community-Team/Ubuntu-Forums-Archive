---
title: "Trouble with DBus, ConsoleKit, NetworkManager, and nm-applet"
date: 2011-07-21
forum: Networking &amp; Wireless
---

### Post by bytbox on 2011-07-21
I'm attempting to run nm-applet outside of gnome (I use dwm w/ slim). When nm-applet is run as my normal user, I get 'connection activation failed: No user settings service available'. When run as root, nm-applet works properly.

My .xinitrc:

```

exec ck-launch-session dbus-launch --sh-syntax --exit-with-session ~/.startdwm
```

My .startdwm:

```
dwm/dwm | {
    nitrogen --restore
    stalonetray --kludges force_icons_size &
    eval `dbus-launch gnome-keyring-daemon`
    dbus-launch gnome-settings-daemon
    dbus-launch gnome-volume-control-applet &
    dbus-launch gnome-power-manager &
    dbus-launch nm-applet --sm-disable &
}
```

---

