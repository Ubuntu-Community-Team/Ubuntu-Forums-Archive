---
title: "MPlayer crashes.. and black Totem..."
date: 2007-02-03
forum: Multimedia &amp; Video
---

### Post by uterrorista on 2007-02-03
**(1) **Now the **MPlayer crashes** when i try to open any kind of movie with it..
**What can be the problem???**

I can open and watch videos with VLC.. 
[B]
(2) [/B]but **not Totem **> i ear the sound but the** images stays black** and when i resise the window i can see image flashes, but the returns to the black image,..

---

### Post by taurus on 2007-02-03
Did you install the codecs before you try to play your video with either mplayer or totem?  And try to play that movie with mplayer from a terminal so you can see what's the problem is.

Applications -> Accessories -> Terminal
```
gmplayer **filename.avi**
```

---

### Post by uterrorista on 2007-02-03
> qaz@blue:~/Desktop$ gmplayer hillclimb.wmv
MPlayer 1.0rc1-4.1.2 (C) 2000-2006 MPlayer Team
CPU: Genuine Intel(R) CPU           T2400  @ 1.83GHz (Family: 6, Model: 14, Stepping: 8)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
98 audio & 216 video codecs
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.
[skin] file ( /usr/share/mplayer/skins/default/skin ) not found.
Skin not found (default).

thanks... what's the problem?
in the past i could open it...

---

### Post by taurus on 2007-02-03
The problem is the skin for your mplayer.  From a terminal, edit ~/.mplayer/gui.conf

```
gedit ~/.mplayer/gui.conf
```
and replace the current "gui_skin =" in there with this.

```
gui_skin = "Blue"
```
Save it and see if you can play that video again.

```
gmplayer ~/Desktop/hillclimb.wmv
```

---

### Post by uterrorista on 2007-02-03
i went to Synaptic Package Manager and installed MPlayer skins..
one problem solved
[SIZE="7"]thanks taurus[/SIZE]
but i still have a problem with totem... the image stays black...

---

### Post by taurus on 2007-02-03
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

