---
title: "Spotify with conky/gnome-applet etc"
date: 2009-08-29
forum: Multimedia Software
---

### Post by mathyou on 2009-08-29
Hi,

Just wondering if anyone knows of a way to display song info from spotify in the panel or in conky? Would be useful as then I don't to open it up to find the name of a song which catches my ear.

cheers,
matt

---

### Post by milouse1664 on 2011-11-04
Hello,

You can get it working with creating a script containing the following code :

```
#!/bin/bash

echo `dbus-send --print-reply --dest=org.mpris.MediaPlayer2.spotify /org/mpris/MediaPlayer2 org.freedesktop.DBus.Properties.Get string:'org.mpris.MediaPlayer2.Player' string:'Metadata'|egrep -A 2 "artist"|egrep -v "artist"|egrep -v "array"|cut -b 27-|cut -d '"' -f 1|egrep -v ^$` "-" `dbus-send --print-reply --dest=org.mpris.MediaPlayer2.spotify /org/mpris/MediaPlayer2 org.freedesktop.DBus.Properties.Get string:'org.mpris.MediaPlayer2.Player' string:'Metadata'|egrep -A 1 "title"|egrep -v "title"|cut -b 44-|cut -d '"' -f 1|egrep -v ^$`

```

And calling it with an execi command from your .conkyrc.

---

### Post by athena2560 on 2011-12-31
I apologize for resurrecting a zombie thread, but, I am having trouble getting the scripts to work; it tells me that it cannot find the output.  Is there a plugin that i'm missing?

---

