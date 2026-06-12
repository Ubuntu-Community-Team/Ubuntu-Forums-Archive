---
title: "VLC causes logout (nvidia beta driver screen shows up)"
date: 2010-11-25
forum: Multimedia Software
---

### Post by mrferos on 2010-11-25
The title pretty much sums it up, when I try to open VLC (as well as Dragon Player, tried it as an alternative) it causes the screen to go black and popup with "Nvidia beta driver" and then back to my login screen. 

Similarly this happens when opening Skype, it does not however happen when I open Movie Player so I'm inclined to believe it's a bug within the drivers themselves and somehow the way that VLC, Dragon Player and Skype choose to interface with my video card force this error. 

Any help would be greatly appreciated. It's not THAT big of a problem since I'm not a big Skype user and Movie Player plays all the formats I actively use but it lacks audio when I play m2ts video files.

---

### Post by tvboxspy on 2010-11-25
One of the overlay drivers does this on nvidia.

Try changing Tools->Preferences.

Select Video and if output set to default try one of the others.

---

### Post by mrferos on 2010-11-26
> **tvboxspy said:**
> One of the overlay drivers does this on nvidia.

Try changing Tools->Preferences.

Select Video and if output set to default try one of the others.

Where exactly? I'm going through NVIDIA X Server settings and there's no option for overly drivers so I guess you mean on VLC itself? The problem is when I open VLC it'll automatically take me to a login screen.

---

### Post by mc4man on 2010-11-26
If you are saying that you can't open vlc or dragon player at all (not trying to play anything), then it has little to do with the video output.
The only thing those 2 apps have in common is Qt4.

Open a terminal, try this (if it plays then Ctrl+q to exit
vlc -Idummy /path/to/a/filename
or (same thing as -Idummy 
cvlc /path/to/a/filename

Ex
> vlc -Idummy /home/doug/Videos/sintel.mp4
VLC media player 1.2.0-git Twoflower (revision exported)
Blocked: call to unsetenv("DBUS_ACTIVATION_ADDRESS")
Blocked: call to unsetenv("DBUS_ACTIVATION_BUS_TYPE")
[0x8edec64] dummy interface: using the dummy interface module...

edit:
similar post
[http://ubuntuforums.org/showthread.php?p=10166699#post10166699](http://ubuntuforums.org/showthread.php?p=10166699#post10166699)

---

### Post by tvboxspy on 2010-11-26
It is the XXMC video driver that causes it.

The bug only appeared after I installed xine media player. But I could open VLC and change the setting.

I believe only MPEG files use it. Try opening a xvid or other mpeg-4 file.

---

