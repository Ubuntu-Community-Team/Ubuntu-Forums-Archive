---
title: "PulseAudio applet for KDE"
date: 2010-11-15
forum: Multimedia Software
---

### Post by insane2600tt on 2010-11-15
Hi there! I've found this very useful for gnome
```
http://code.google.com/p/gnome-pulse-applet/
```

but I was wondering whether it exists the equivalent for KDE; as of today I use this workaround: I've created a file called [HTML]lunchPAVU.desktop[/HTML] with this content into my [HTML]~/.kde/Autostart/[/HTML] directory. 
```

[Desktop Entry]
Exec[$e]=sleep 30; ksystraycmd pavucontrol
Icon=xfce-sound
Name=PulseAudio Volume Control
Name[en_US]=PulseAudio Volume Control
StartupNotify=false
Terminal=false
Type=Application
X-KDE-SubstituteUID=false

```

Any better idea?

Thanks!

---

### Post by lykwydchykyn on 2010-11-15
Since I'm not using gnome or xfce, I don't know what those particular applets provide that you're looking for.  But as far as a better volume control for KDE, there's a plasmoid you can get through the "get new plasma widgets" dialog (or directly from kde-look.org) called "veromix" that does a lot better with pulseaudio than the default mixer.

Once you install it, you can either put it directly on the panel or enable it in the system tray.

---

### Post by insane2600tt on 2010-11-15
Great! Thank you! This solved my issue in KDE4!!

How about KDE3.5 ? I have a couple of systems where I run the old KDE because users like it better than 4...

Thank you!

---

### Post by lykwydchykyn on 2010-11-15
That I don't know; haven't seen kde 3 in about 2 years.

---

