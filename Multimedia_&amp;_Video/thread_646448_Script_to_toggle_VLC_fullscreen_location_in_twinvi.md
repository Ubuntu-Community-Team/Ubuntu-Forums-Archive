---
title: "Script to toggle VLC fullscreen location in twinview dual display"
date: 2007-12-21
forum: Multimedia &amp; Video
---

### Post by chewearn on 2007-12-21
Hi, just thought I will post a script to help those in same situation.  If you have:
1. Two displays
2. nvidia with twinview set-up
3. Watch you video with VLC
4. Sometimes, you want VLC fullscreen to be on the first screen, and sometimes on the second screen
5. Got tried of multiple mouse-clicks to change the VLC preference to switch the fullscreen location

Here is a bash script to toggle the fullscreen location of VLC.

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
```Note:
1. I added a panel launcher to run this script, so each time I only need to click on it to switch the fullscreen location

2. You need to install zenity so the script can display dialog messages:
```
sudo aptitude install zenity
```3. This script change the xvideo-xineramascreen attribute in ~/.vlc/vlcrc, which correspond to the xvideo module; if you VLC output module is set to another, you need to modify the script to your situation.

---

### Post by ariel on 2007-12-29
Thanks astalavista! Same problem here.

The script fixed it. BTW, it does not work with VLC 0.9daily, and I also had to choose "alternate full screen method". My second twinview screen is my tv and has a different resolution than the main monitor, and without the alternate method vlc messes up the resolution in the TV (only shows a fraction of the image)

---

### Post by chewearn on 2007-12-29
> **ariel said:**
> Thanks astalavista! Same problem here.

The script fixed it. BTW, it does not work with VLC 0.9daily, and I also had to choose "alternate full screen method". My second twinview screen is my tv and has a different resolution than the main monitor, and without the alternate method vlc messes up the resolution in the TV (only shows a fraction of the image)

Thanks for the heads-up.  Feel free to post modifications to the script to get it working.

---

### Post by flatko on 2008-05-06
I have to say it - it works without any modification. At least for me :)
I'm using 2 soundcards. I can browse the web and listen to music in my room, until tv-out + 2nd sound card is going to the other room for watching movies... Linux rullz :)

---

