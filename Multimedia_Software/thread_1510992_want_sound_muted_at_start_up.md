---
title: "want sound muted at start up"
date: 2010-06-16
forum: Multimedia Software
---

### Post by bacchusmarsh on 2010-06-16
I have two laptops, one has sound muted at start up (karmic), like in [this thread ]("http://ubuntuforums.org/showthread.php?t=1089948&highlight=make+sound+mute+shutdown"), and i like it 

and in one the sound is not muted and i want it too be (lucid), like in [this thread]("http://ubuntuforums.org/showthread.php?t=675134&highlight=make+sound+mute+shutdown").

how do i set to mute on startup (or shutdown to be more precise)?

thanks.

---

### Post by dino99 on 2010-06-16
use gconf-editor to set your prefs

---

### Post by bacchusmarsh on 2010-06-16
ok awesome thanks.

so for others; i typed sudo gconf-editor into terminal and found indicator-sound under apps, then checked the mute box.

edit:actually that did not work, whether i have sound mute set to true or false it makes no difference (in Lucid on eeepc)

---

### Post by bacchusmarsh on 2010-06-18
in fact i can't even find the indicator-sound preference in the gconf-editor on Karmic?

any chance of further assistance...?

---

### Post by AutoStatic on 2010-06-18
[LIST]
[*]Open a terminal
[*]Mute your sound
[*]enter the following command in the terminal:
```
alsactl store 0 -f ~/.asound.state
```
[/LIST]

Now your sound should be muted everytime you log in.

---

### Post by bacchusmarsh on 2010-06-18
thanks but no cigar.

do i need to edit a conf file as well?... to save settings i mean...

---

### Post by Yellow Pasque on 2010-06-18
You could add a command like the following to /etc/rc.local
```
amixer -c 0 sset Master playback 0%
```

---

### Post by AutoStatic on 2010-06-22
Personally I wouldn't advise adding userspace stuff to rc.local. Concerning the amixer command, I would add it to the Startup Applications (System - Preferences - Startup Applications).
No idea why the alsactl command doesn't work, works for me.

---

### Post by Richard85 on 2010-06-22
This might be the obvious solution but 
System > Preferences > Sounds > Sound Theme: No Sounds

---

### Post by bacchusmarsh on 2010-06-22
thanks to you all, i have kind of given up for now, after trying those first few suggestions. 
problem is my terminal abilities are pretty much at the 'cut and paste' level, so i would not know how to adapt your suggestions to my specific case. but i will use it as a learning exercise when i have a little time again...
Richard: thanks, i did that once before when my startup sounds where crackly and forgot about it. it will do for now... though what i was trying to do was have all sounds (movies, music as well as startup) reset to a particular level, whenever i start up, to avoid sudden loud outbursts!

---

