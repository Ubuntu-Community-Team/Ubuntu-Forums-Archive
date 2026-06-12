---
title: "DVD auto playback in VLC 9.10"
date: 2010-02-22
forum: Multimedia Software
---

### Post by mortalic on 2010-02-22
I hope I'm missing something simple because all i want is when a DVD is mounted is for VLC to popup and start playing.  As it sits right now VLC doesn't even open.  I've found lot's of instructions for versions pre 9.10 but they all don't work.  
Anyone done this before?

---

### Post by mc4man on 2010-02-22
It's in file management -> media which is a menu item that's hidden by default. Half a dozen ways to access, ect., here's one, in terminal

```
nautilus-file-management-properties
```

to enable in applications  go 
```
alacarte
```
and look under system -> preferences, check the box

---

### Post by J_Stanton on 2010-02-22
or open your home folder and go to edit-preferences-media tab and select vlc as dvd default.

---

### Post by wojox on 2010-02-22
And you've got everything installed for vlc:

```
sudo apt-get update && sudo apt-get install libdvdcss2 gxine libxine1-ffmpeg
```

---

