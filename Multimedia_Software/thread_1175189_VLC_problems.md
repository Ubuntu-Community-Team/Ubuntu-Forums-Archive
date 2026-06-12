---
title: "VLC problems"
date: 2009-05-31
forum: Multimedia Software
---

### Post by aloasi on 2009-05-31
I have been having VLC crash everytime i try to play any type of video. This is what i get if I run VLC from the command line

```
hector@hector-desktop:~$ vlc
VLC media player 1.0.0-rc2 Goldeneye
[0x1213db8] main interface error: no interface module matched "globalhotkeys,none"
[0x1213db8] main interface error: no suitable interface module
[0xfda888] main libvlc error: interface "globalhotkeys,none" initialization failed
/home/hector/.themes/still-unamed/gtk-2.0/panel.rc:96: Unable to locate image file in pixmap_path: "Panel/panelnutton4.png"
/home/hector/.themes/still-unamed/gtk-2.0/panel.rc:99: Background image options specified without filename
/home/hector/.themes/still-unamed/gtk-2.0/gtkrc:1532: Unable to locate image file in pixmap_path: "Tabs/notebookright.png"
/home/hector/.themes/still-unamed/gtk-2.0/gtkrc:1542: Background image options specified without filename
/home/hector/.themes/still-unamed/gtk-2.0/gtkrc:1892: Invalid symbolic color 'selected_bg_color'
/home/hector/.themes/still-unamed/gtk-2.0/gtkrc:1892: error: invalid identifier `selected_bg_color', expected valid identifier
Interface initialization failed

```
Anything would be appreciated. Thank you

---

### Post by Steelmourne on 2009-05-31
Seeing as that is the release candidate of vlc, it seems you are missing the gui or interface. If you've compiled vlc from source recompile it again.

---

### Post by aloasi on 2009-06-01
Hello, i got vlc from a ppa. Thank you will try everything now.

---

