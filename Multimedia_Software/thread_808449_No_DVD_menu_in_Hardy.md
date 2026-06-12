---
title: "No DVD menu in Hardy"
date: 2008-05-26
forum: Multimedia Software
---

### Post by almalaci on 2008-05-26
I just did a fresh install of Hardy and none of the media players (VLC, totem, mplayer) has menus and navigation working. Some, like VLC gets to the root menu of the DVD but the menus cannot be selected.
I have the following installed:
libdvdcss2 libdvdread3 libdvdnav4 vlc

Any ideas?

---

### Post by mc4man on 2008-05-26
The only one out of your list that does menus is vlc and you have what you need. It's been awhile since I had an unmodified hardy but _possibly_ your being affected by the launch command for vlc. You could try changing the launch command -  r. click on applications -> edit menus -> choose sound and video on left side, right click on vlc on right side -> properties and change command to this from vlc %U (or %F)
```
vlc %m
```
You may be happier if vlc was your default movie player, an easy way is here and also involves changing the launch command. section 4/5
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)  (the -volume 512 part of command is optional)
If you have any further navigation issues then adjust the vlc.desktops as here
[http://ubuntuforums.org/showthread.php?t=733559](http://ubuntuforums.org/showthread.php?t=733559)  post 8
It's not mentioned in sticky but to switch  media defaults, again in edit menus -> preferences enable file management
You could also install totem-xine (supports menus). After doing so in the terminal run ```
sudo update-alternatives --config totem
``` choose option 2 and totem-xine will be your default totem player

---

### Post by almalaci on 2008-05-27
Great, it did the trick! I realised in the meantime that opening a disc/DVD iso file FROM vlc works fine, only when I try to open DVD's from nautilus that it doesn't work. So thanks a lot and also for the useful links!

---

### Post by Octagonal on 2008-05-27
Thanks mc4man, I had this exact problem as well and "vlc %m" resolved it perfectly.

---

