---
title: "how to set default dvd player in lucid?"
date: 2010-06-18
forum: Multimedia Software
---

### Post by boarder428 on 2010-06-18
I would like to set xine as my default player for DVD playback and cannot figure out how.  I have read other posts that state to right click on file>properties>open with but do not seem to have the open with option when right clicking a dvd that is in my dvd drive.  I would also like to change the  open with option in the right click menu if anybody could help me with that.  The current option is to open with movie player, and movie player cannot seem to find additional plug ins to open file with.
Thanks
Corey

---

### Post by mc4man on 2010-06-18
I'm not to sure xine will respond correctly if set as default dvd player - **referring to dvd video media**

This is set in file management -> media, many ways to get to, one is
```
nautilus-file-management-properties
```

you could try using the default xine (won't be listed, use xine or there's a way to register xine - not going to bother to say

Most likely you'll need to create a new launcher for xine, either an userapp.desktop or more 'traditional' .desktop

For userapp just go to the ...media and choose under dvd media -> open with other application -> use a custom command
for command
```
xine dvd://
```
Should show up as a choice named xine.

A bit cleaner method that I prefer is this - 

```
cp /usr/share/applications/xine.desktop ~/.local/share/applications/xine-dvd.desktop


```
```
 gedit ~/.local/share/applications/xine-dvd.desktop
```

Make the .desktop look like this (blue are edited lines

> [Desktop Entry]
Encoding=UTF-8
[COLOR="Blue"]Name=xine dvd player[/COLOR]
Comment=Video Player
[COLOR="Blue"]Exec=xine dvd://[/COLOR]
[COLOR="Blue"]MimeType=video/mpeg;video/quicktime;video/x-msvideo;video/x-anim;audio/x-mp3;audio/x-mp2;x-content/video-dvd;[/COLOR]
Icon=xine
Terminal=false
Type=Application
Categories=Application;AudioVideo;Player;

```
gedit ~/.local/share/applications/mimeapps.list
```
Look for the line in blue and add to beginning of line ```
xine-dvd.desktop;
```
(pay attention to formatting - no spaces, each entry ends with a ; 
first listed is the default

> [COLOR="Blue"]x-content/video-dvd=[/COLOR]xine-dvd.desktop;vlc.desktop;userapp-dvdrip-Y1D4CV.desktop;totem-xine.desktop;totem.desktop;

restart to add and see

Edit:
most likely xine will only work as default(autorun) dvd player for 1 device (as set in xine -> settings), to use with more may be possible with a script.

---

### Post by boarder428 on 2010-06-19
well that seemed to work!  I just wish I had some clue to what we just did there! LOL!  Where do you learn how to run all these commands?  I've been using Ubuntu for about a year now and would have never figured that out on my own!
Thanks!
Corey

---

