---
title: "mplayer &amp; gnome3"
date: 2012-07-08
forum: Multimedia Software
---

### Post by yellowpaper on 2012-07-08
I have a little question. I cant "connect" mplayer (not the gui) with the video-files in gnome3. Even exists mplayer(not gui) if i try "open with other application".
What is the problem with this?.

Bye!

---

### Post by mc4man on 2012-07-08
Because the context menus only show .desktops (launchers), there isn't one installed by default for the cli mplayer

You'll need to create one (or more
In the past if you used the 'custom command' option it would create a .desktop for you, with that option removed you'll need to use alternate means

I just create them here myself, can do it better  that the other ways currently available, though [http://www.florian-diesch.de/software/arronax/](http://www.florian-diesch.de/software/arronax/) is starting to do a very good job of it

Ex. here, I use 2 .desktops for mplayer, one for all audio/video files, one for playlists.
After creating I also drag the .desktops on to the unity launcher for DnD of their supported mimetypes
Because I use for both audio & video I choose to have mplayer run in a terminal, otherwise no way to control for audio files & audio playlists

The Icon= line are icons of my own chossing, have nothing really to do with mplayer & aren't in 12.04 anyway, if copying these you'd need to change

The Mimetypes= line in mplayer1.desktop is very long in forum codebox..

I think you could find arronax very useful, keep in mind that to show in the context menu the Exec= line must end in %<letter>, valid & most useful are - 
%U
%u
%f

So for general purpose I'd go (assumes ~/.local/share/applications exists, usually does
You can add mplayer options to the Exec= line though I control that thru ~/.mplayer/config
```
gedit ~/.local/share/applications/mplayer1.desktop
```
```

[Desktop Entry]
Version=1.0
Type=Application
Terminal=true
Exec=mplayer %U
Name=Mplayer1
Icon=apple-green.png
MimeType=video/dv;video/mpeg;video/x-mpeg;video/msvideo;video/quicktime;video/x-anim;video/x-avi;video/x-ms-asf;video/x-ms-wmv;video/x-msvideo;video/x-nsv;video/x-flc;video/x-fli;video/x-flv;video/vnd.rn-realvideo;video/mp4;video/mp4v-es;video/mp2t;application/ogg;application/x-ogg;application/x-matroska;audio/x-mp3;audio/x-mpeg;audio/mpeg;audio/x-wav;audio/x-m4a;audio/x-ms-asf;audio/x-ms-asx;audio/x-ms-wax;application/vnd.rn-realmedia;audio/x-real-audio;audio/x-pn-realaudio;application/x-flac;audio/x-flac;application/x-shockwave-flash;misc/ultravox;audio/vnd.rn-realaudio;audio/x-pn-aiff;audio/x-pn-au;audio/x-pn-wav;audio/x-pn-windows-acm;image/vnd.rn-realpix;audio/x-pn-realaudio-plugin;application/x-extension-mp4;audio/mp4;x-content/video-vcd;x-content/video-svcd;x-content/video-dvd;x-content/audio-cdda;x-content/audio-player;audio/x-ape;audio/x-tta;
```

For a playlist only mplayer
```
gedit ~/.local/share/applications/mplayer2.desktop
```

```
[Desktop Entry]
Version=1.0
Type=Application
Terminal=true
Exec=mplayer -playlist %U
Name=Mplayer List
Icon=apple-red
MimeType=audio/x-mpegurl;audio/x-scpls;
```

Name= can be as desired
Icon= can be as desired, full path if not in /usr/share/pixmaps or /usr/share/app-install/icons
Mimetype= can be as needed

---

### Post by yellowpaper on 2012-07-08
Thanks! It works it WORKS muajajajaja :D . You threw a magic... (Spanish= Tiraste una magia...) ...
I did all of this but i copy the file to another  place...

---

