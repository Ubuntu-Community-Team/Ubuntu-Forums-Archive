---
title: "Video playback issues - vlc"
date: 2009-11-14
forum: Multimedia Software
---

### Post by maxclimber1w on 2009-11-14
When I attempt to play local videos I have two problems:

1) There is a line of 'choppiness' about 2/3rds up the frame. This occurs in vlc and other players as well.

2) vlc starts in a fullscreen-like interface, without the window border visible. This started when I chose the option "window decorations" in the vlc video preferences menu, but now is persistent despite unchecking that box.


I'm running vlc 1.0.2, linux Mint 7.0 (ubuntu 9.04), Quad core 2.4ghz, 3.2gb ram, Radeon HD 2400 Pro video card. 

Any ideas?

---

### Post by maxclimber1w on 2009-11-15
This is the output I get when I play a 720p .mkv file:

```
[0x95cead0] swscale scale error: could not init SwScaler and/or allocate memory
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one

```

---

### Post by maxclimber1w on 2009-11-15
bump! Help!

---

### Post by terdon on 2009-12-05
I had the same problem, solve by deleting (or renaming) the $HOME/.config/vlc/ directory:

```
mv ~/.config/vlc/vlc .
```

---

### Post by Rudias on 2011-04-02
Start VLC and click on Settings, then Preferences.

o Expand Video and then expand Output modules. You will notice several options for output device.

o Select the item Output modules, and notice the checkbox at the bottom right that says Advanced options. Check the box, and now you have the option to select a different output device.

o Pick X11 video output

o Click on Save and you are set!

* MPlayer Users (Mplayer is not installed by default)

o Start Mplayer

o Right-click on the screen and select Preferences

o Select the Video tab and under Available Drivers select “X11 (XImage/Shm)”

o Click Save and restart the program for the setting to take effect.

---

