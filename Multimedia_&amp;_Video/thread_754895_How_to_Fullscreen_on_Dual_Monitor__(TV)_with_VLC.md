---
title: "How to Fullscreen on Dual Monitor  (TV) with VLC"
date: 2008-04-14
forum: Multimedia &amp; Video
---

### Post by mgybran on 2008-04-14
I have twin dual screen set up for my Feisty Faun.  When opening an avi film with Mplayer (backend xine) it automatically opens up on my second screen of TV.  I can then double click it and it goes into fullscreen.  When doing the same with VLC for my iso and img files the film opens on my first monitor and I have to move the film output to my TV output.  

When double clicking it to take it to Fullscreen the fullscreen output switches back to the monitor one (PC monitor).  Has anyone else had the problem and managed to to resolve it?  I can't see anywhere in the VLC controls where I can set the fullscreen output location.

Thanks in advance

---

### Post by chewearn on 2008-04-15
Under:
Settings > Preferences > Video > Output modules

Find out the output module VLC is using (or just trial and error).  E.g. if VLC is using Xvideo, then:
> XVideo > Screen for fullscreen mode > change "0" to "1" for the second screen.

Because the settings are deep in the Preferences, it is a hassle to change it whenever you want to switch first and second screen.  So, I have previously written a script to take care of this (but I don't use this script anymore, so if there are errors, tell me so I can try to fix it):

```

#!/bin/bash

VLCRUNNING=`ps -e | grep wxvlc`
if [ "$VLCRUNNING" ]; then
  zenity --error  --title "Toggle VLC fullscreen" --text="VLC is running!  Close all instances of VLC first."
fi

CURRENTSTATE=`cat ~/.vlc/vlcrc | grep  xvideo-xineramascreen | cut -c24`

if [ "$CURRENTSTATE" ]; then
  # Current state is #xvideo-xineramascreen=0
  sed -i "s/#xvideo-xineramascreen=0/xvideo-xineramascreen=1/" ~/.vlc/vlcrc
  zenity --info --title "Toggle VLC fullscreen" --text "        Set to screen 1        "
else
  # Current state is xvideo-xineramascreen=1
  sed -i "s/xvideo-xineramascreen=1/#xvideo-xineramascreen=0/" ~/.vlc/vlcrc 
  zenity --info --title "Toggle VLC fullscreen" --text "        Set to screen 0        "
fi

```You need to install zenity to get the messagebox for this script:
```
sudo apt-get install zenity
```

---

### Post by mgybran on 2008-04-17
That was just the ticket.  I didn't use the script.  Switching to '1' in the xvideo was just what I needed.  Many THANKS

---

### Post by Ux64 on 2008-05-23
> **AstalaVista said:**
> Because the settings are deep in the Preferences, it is a hassle to change it whenever you want to switch first and second screen.

Yep, that sucks. But I wonder why it was working flawlessly with Gutsy Gibbon. When I upgraded to Hardy it stopped working again. Now I have to change that prerence number. Why it can not be automaticly detected which screen should be used?

---

