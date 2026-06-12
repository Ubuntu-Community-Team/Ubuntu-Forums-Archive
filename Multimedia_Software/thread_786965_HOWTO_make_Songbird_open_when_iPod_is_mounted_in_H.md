---
title: "HOWTO: make Songbird open when iPod is mounted in Hardy."
date: 2008-05-08
forum: Multimedia Software
---

### Post by dbcoolio on 2008-05-08
So they moved the config that sets up app for when a music player is mounted from the Removable Drives and Media GUI to nautilus' Edit->preferences->media.  I think it will open it up to more options, and better organization for that sort of thing later, but for now it isn't exactly feature complete.  for example, right now you can have it open with rhythmbox, ask for input, or do nothing.  Following some other threads I figured out how to add more options to that menu.

first you need to make sure songbird has a .desktop file in the /usr/share/applications/ directory.  here's a sample one:

```

[Desktop Entry]
Name=Songbird Music Player
GenericName=Songbird
Comment=Mozilla's Answer to iTunes
Exec=/home/horizon/opt/Songbird/songbird _
Icon=/home/horizon/linux stuff/icons/songband.png
Terminal=false
Type=Application
Categories=Music;iPod;Mozilla
MimeType=application/x-ogg;application/ogg;audio/x-scpls;audio/x-mp3;audio/x-mpeg;audio/mpeg;audio/x-mpegurl;application/x-flac;x-content/audio-cdda;x-content/audio-player;
```

Of course change the paths to the execute path for songbird and the icon path.  The underscore makes it so that the program won't try to read in the path as normal media.

then you need to edit /etc/gnome/defaults.list so that:

```
x-content/audio-player=songbird.desktop
```

Then go in to the Nautilus preferences menu and choose Songbird Music Player.

this should work for lots of other stuff too.

---

### Post by jmjohn on 2008-07-22
Hmm.  I have followed these steps, modified the desktop file to include the MimeType entry as well as the sonbird_ entry, and added the x-content/audio-player=sonbird.desktop to the defaults.list file but still am unable to use Songbird as the default for MP3s.

Do I need to add a Mime listener thingy?

-glass.dimly

---

