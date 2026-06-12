---
title: "VLC 2.0.5, D-Bus not there"
date: 2013-01-17
forum: Multimedia Software
---

### Post by Sinopa on 2013-01-17
Hi.

I just re-installed Xubuntu 12.04 and VLC 2.0.5. For some strange reason I can't find Dbus under *Tools>Interface>Control Interfaces* in VLC now. Does anyone know why? Have I forgotten something?  How I can activate Dbus in VLC 2.0.5?

---

### Post by Yellow Pasque on 2013-01-17
I think VLC is moving towards MPRIS support, but mpris doesn't recognize VLC.
```
sudo apt-get install mpris-remote
vlc --control dbus
```

---

### Post by mc4man on 2013-01-17
> **Sinopa said:**
> Hi.

I just re-installed Xubuntu 12.04 and VLC 2.0.5. For some strange reason I can't find Dbus under *Tools>Interface>Control Interfaces* in VLC now. Does anyone know why? Have I forgotten something?  How I can activate Dbus in VLC 2.0.5?
I'd guess it's already so. What do you want to do?

(- vlc should be in the sound menu, if not can be added in dconf-editor
com.canonical.indicator.sound interested-media-players
Though don't know if ^ relates to xubuntu & or 12.04

Some dbus 'commands' can be seen with (assumes vlc is open, am on 13.04 so 12.04??
```
qdbus org.mpris.MediaPlayer2.vlc /org/mpris/MediaPlayer2
```

Ex.
```
qdbus org.mpris.MediaPlayer2.vlc /org/mpris/MediaPlayer2 org.mpris.MediaPlayer2.Player.Previous
```
or same
```
 dbus-send --print-reply --dest=org.mpris.MediaPlayer2.vlc /org/mpris/MediaPlayer2 org.mpris.MediaPlayer2.Player.Previous
```

ect.

---

