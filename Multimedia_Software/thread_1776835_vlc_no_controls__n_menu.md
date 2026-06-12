---
title: "vlc no controls / n menu"
date: 2011-06-06
forum: Multimedia Software
---

### Post by holiday on 2011-06-06
I can start vlc by clicking on an avi file (for example), but there are no controls, no menu whatsoever. 

How do I get the menu back if there's no menu?

---

### Post by ron999 on 2011-06-06
> **holiday said:**
> 
How do I get the menu back if there's no menu?
Hi
While the video is playing...
**Right-click** on the picture...
Then 'View >'...
Then un-tick 'Minimal View'.;)

---

### Post by holiday on 2011-06-06
Thanks, Ron, but right click doesn't bring up the menu. Some shortcuts work so maybe there's a key to bring up preferences? 

The window frame says XVideo output. Haven't seen that before.

---

### Post by ron999 on 2011-06-06
Hi
Look in folder .config > vlc
Find the file:-
vlc-qt-interface
Re-name it:-
vlc-qt-interface.old
Then re-start VLC from the main menu.

---

### Post by holiday on 2011-06-06
Still no. I moved the vlcrc file out of the way too.

Starting from the Applications menu has no effect, but from the commandline I get this:


vaio:~/.config/vlc$ vlc &
[1] 3598
VLC media player 1.0.6 Goldeneye
[0x98ca1d8] main interface: creating httpd
[0x98d3958] telnet interface: using the VLM interface plugin...
[0x98d3958] telnet interface: telnet interface started on interface  4212
B: command not found

So I tried in a browser [http://localhost:4212](http://localhost:4212) - my best guess, but I get nothing. Not even a timeout.

---

### Post by mc4man on 2011-06-06
Just open a normal terminal and 
```
vlc -Iqt4
```
It should open as normal, if so 
Tools > Preferences > click the "All", then  Interface > Main interface, set to Default or Qt interface as in screen

Or you could try 
```
vlc -Iqt4 --reset-config --reset-plugins-cache
```

---

### Post by holiday on 2011-06-07
Thanks! That worked.

---

