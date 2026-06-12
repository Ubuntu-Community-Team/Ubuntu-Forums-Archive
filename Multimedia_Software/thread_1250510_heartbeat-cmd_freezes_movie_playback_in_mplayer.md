---
title: "heartbeat-cmd freezes movie playback in mplayer"
date: 2009-08-26
forum: Multimedia Software
---

### Post by Lockheed on 2009-08-26
I use```
heartbeat-cmd="gnome-screensaver-command -p &>/dev/null"
```so that my screen doesn't dim while watching movies in (s)mplayer. 

However, this has very annoying side effect - movie playback freezes for 1-2 seconds few times per minute. If I remove this command from mplayer config, the problem goes away, but the screen dims.

Any ideas?

---

### Post by xtknight on 2009-08-26
nohup nice -n 19 gnome-screensaver-command -p &>/dev/null &

Try this command to attempt to run the program in the background more.

---

### Post by Lockheed on 2009-08-27
> **xtknight said:**
> nohup nice -n 19 gnome-screensaver-command -p &>/dev/null &

Try this command to attempt to run the program in the background more.

When I put this command in the config, mplayer will not run, producing error message:
```
mplayer -noquiet -nofs -sub-fuzziness 1 -identify -slave -vo xv -ao alsa -zoom -nokeepaspect -framedrop -nodr -double -input conf=/usr/share/smplayer/input.conf -stop-xscreensaver -wid 106954767 -monitorpixelaspect 1 -*** -embeddedfonts -***-line-spacing 0 -***-font-scale 1 -***-styles /home/juha/.config/smplayer/styles.*** -fontconfig -font Arial -subcp CP1250 -vid 0 -aid 1 -subpos 100 -cache 2000 -osdlevel 1 -nocorrect-pts -vf-add pp -autoq 6 -vf-add screenshot -slices -channels 2 -af scaletempo,equalizer=0:0:0:0:0:0:0:0:0:0 -softvol -softvol-max 340 /home/juha/Desktop/Down/Season 1/The Unit 1x11 - Exposure.avi

Option nohup needs a parameter at line 8
```

---

