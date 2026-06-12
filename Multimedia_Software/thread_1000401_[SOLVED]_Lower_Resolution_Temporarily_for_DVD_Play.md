---
title: "[SOLVED] Lower Resolution Temporarily for DVD Playback? (Compatibility Mode)"
date: 2008-12-02
forum: Multimedia Software
---

### Post by brntoki on 2008-12-02
For my Ubuntu Intrepid box I have a very low spec system.  The only thing that is problematic, however, is DVD playback.  It works, but it's herky-jerky.  Windows won't play my DVDs on the same system unless I run VLC in 640x480, but it's easy enough to force that resolution specifically for VLC and have it return to native ( 1024x768 ) once exited.

I'd like to know how to achieve this on Intrepid.  I could probably append an xrandr -s 640x480 -r 60 to the beginning of the launch command, but I don't know exactly how to do that (trying in a terminal didn't work -- I'm sure I didn't do it correctly: xrandr -s 640x480 -r 60 vlc)  I guess there must be some separator for the two distinct commands.

Any help greatly appreciated.  And also, if you could help with the fact that changing back to 1024x768 rearranges my panel icons (shoves them to the left instead of centered).


UPDATE: ***Solved***
Okay; I figured out that I just needed a semicolon between the two commands.  I'll just create a launcher for DVD/Video playback with the xrandr command, and then another launcher to switch the resolution back when finished.  This is for my kids' ease of use, as well as the wife's.

UPDATE: 
I guess it wasn't that easy after all.  I thought creating a straightforward launcher would do it, but no dice.  I found that I actually had to start a terminal with the launcher and then put the two others inside quotation marks.  It looks like this:

```
gnome-terminal -x bash -c "xrandr -s 640x480 -r 60 ; vlc"
```

---

### Post by brntoki on 2008-12-03
Okay, after more googling I think what I'm looking for is a bash script.  I have no clue how to.

I tried to make sense of this script and it just isn't clicking for me.  I'm guessing this is close to what I'll need, but don't want to do anything until I can sorta understand it.

```
#!/bin/sh

# run game

res="$(xrandr -q|grep '^\*')"
if [[ "${res:1:1}" != 0 ]]; then
        xrandr -s 0
fi
```

Can anyone break this down for me?

---

