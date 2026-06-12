---
title: "set CVLC to default video player in 11.10"
date: 2012-01-07
forum: Multimedia Software
---

### Post by solitaire on 2012-01-07
OK

This is bugging me!!

How do you set avi, mpg etc... to open with "cvlc" NOT "vlc"?

I could do it in 11.04 and previous versions but not in 11.10!

Currently I've had to open videos using the terminal, it's messy and slow! (Rather just double click the video to playing cvlc.)

Any way to add cvlc to the application list??

---

### Post by mc4man on 2012-01-07
You could start  by making a .desktop & take from there. An example would be this - 
```
gedit ~/.local/share/applications/cvlc.desktop
```

```
[Desktop Entry]
Version=1.0
Name=cvlc player 
Comment=
Exec=cvlc %U
Icon=vlc
Terminal=true
Type=Application
Categories=AudioVideo;Player;
MimeType=video/dv;video/mpeg;video/x-mpeg;video/msvideo;video/quicktime;video/x-anim;video/x-avi;video/x-ms-asf;video/x-ms-wmv;video/x-msvideo;video/x-nsv;video/x-flc;video/x-fllvci;video/x-flv;video/vnd.rn-realvideo;video/mp4;video/mp4v-es;video/mp2t;application/ogg;application/x-ogg;video/x-ogm+ogg;audio/x-vorbis+ogg;application/x-matroska;audio/x-matroska;video/x-matroska;video/webm;audio/webm;audio/x-mp3;audio/x-mpeg;audio/mpeg;audio/x-wav;audio/x-mpegurl;audio/x-scpls;audio/x-m4a;audio/x-ms-asf;audio/x-ms-asx;audio/x-ms-wax;application/vnd.rn-realmedia;audio/x-real-audio;audio/x-pn-realaudio;application/x-flac;audio/x-flac;application/x-shockwave-flash;misc/ultravox;audio/vnd.rn-realaudio;audio/x-pn-aiff;audio/x-pn-au;audio/x-pn-wav;audio/x-pn-windows-acm;image/vnd.rn-realpix;audio/x-pn-realaudio-plugin;application/x-extension-mp4;audio/mp4;audio/amr;audio/amr-wb;x-content/video-vcd;x-content/video-svcd;x-content/video-dvd;x-content/audio-cdda;x-content/audio-player;application/xspf+xml;x-scheme-handler/mms;x-scheme-handler/rtmp;x-scheme-handler/rtsp;

```

Whether after a log out/in it starts showing up in the context menu for your various filetypes is debatable, it does here though I do something that may help that out - 
After creating I drag the .desktop onto the unity launcher where it can act as a DnD for mimetypes listed. 
(shown in screen 1 - the vlc icon is cvlc.desktop, screen 2 show cvlc player showing thru the r. click context on a .wma I just dl'ed to check wmalossless support in vlc

**Notes on the .desktop** - 
The "Terminal=true" will open a terminal that will last the duration of the file then auto close. If you just want as a background then set to false

The %U in the Exec= line will allow use as a DnD launcher & allow the cvlc player to show up on the right click > **Properties** menu

The "Name=" line can be whatever you want

The "Icon=" can be something other that vlc, if so then fullpath to icon  or if desired leave blank

(- if you have issue getting the player to appear on the r. click context menus then if a few log out/in don't resolve you can 'force' by adding cvlc.desktop to various lines in ~/.local/share/applications/mimeapps.list
If unclear on how then just ask

---

### Post by solitaire on 2012-01-08
Many thanks!!

That's what i wanted ^_^

Might only be a few mHz, but it makes all the difference between "cvlc" than "vlc" when playing 720p MKV's smoothly or not on my Celeron Laptop... ^_^

---

