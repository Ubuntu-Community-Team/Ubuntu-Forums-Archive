---
title: "Are NVidia graphics really easier?"
date: 2006-06-26
forum: Multimedia &amp; Video
---

### Post by PuleX on 2006-06-26
I have been using Linux and Ubuntu for over 1,5 years now, and I haven't considered booting into Windows for at least 1 year. But there is one Windows 'feature' I fondly remember: good drivers for my ATI graphics cardwith easy configurable TV-out... 
Under Linux I have to boot my pc, then connect my tv-out cable to the tv, restart X and then play a video file on the tv with something like *DISPLAY=:0,1 xine /path/to/file*. Especially the restart-X-and-login-again part is irritating.  ](*,) 

Now, I am planning to upgrade my PC in the near future (extra RAM, new HD), and I was wondering if an nVidia graphics card would make my Linux life easier. I know the drivers are better. But do simple things like connecting my pc to a tv and playing an AVI file with DISPLAY=:0,1 simply work? Without first restarting X? If that is the case, I may upgrade. If not, then the ATI card is good enough for now. 

I hope someone can enlighten me. thanks in advance.  :)

---

### Post by tseliot on 2006-06-26
I use an Nvidia card and I have to restart X every time I enable my tvout because I need to modify the xorg.conf:

```
Section "ServerLayout"
    Identifier  "Simple Layout" 
    Screen 0 "Screen[0]" 
    [COLOR="Red"]#[/COLOR]Screen 1 "Screen[1]" RightOf "Screen[0]" 
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
EndSection
```

I just remove the # and log out, press CTRL+ALT+Backspace and log in again.

In that way I can make my mouse cursor pass from the right of my screen to the TV screen.

However if I wanted I could avoid doing that thing every time I need the tvout. I could just leave the xorg.conf without the # (every time I boot) but then my mouse cursor would be able to move out of the screen (even if the TV screen is not connected) which is annoying.


P.S. I think your ati card is good enough. There's no need to buy an Nvidia card

---

### Post by PuleX on 2006-06-27
Ok, thanks for the feedback. I'll just do a normal upgrade then.  :)

---

