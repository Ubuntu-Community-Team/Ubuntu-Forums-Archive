---
title: "All media (audio &amp; video) result in X crashing/restarting..."
date: 2006-12-09
forum: Multimedia &amp; Video
---

### Post by JonoMG on 2006-12-09
Firstly, let me point out I am new to any type of Linux... Ubuntu is my first installation and it has now been on my PC for about 3 days.

I am loving it... except for one small thing.

Whenever I attempt to play ANY type of media file X is crashing, I get jumbled colour splash screen (don't know if this is just X restarting or a symptom of the problem) and then I am presented with the login window.

When I say any media file, I mean any... I have tried Xvid, Vob, MP3, OGG. I have tried using Totem and VLC - both suffer the same fate. ](*,) *Update... I have tried playing some MP3's in Rhythmbox Music Player and no crash... don't know if that helps in the diagnosis.*

The frustrating thing is that I don't even know where to start looking. I am happy to post log files, further description, anything.

I really want this installation to work and would appreciate any help people want to give.

TIA. Cheers,

Jono


***********************************************

Second update - reset my xorg.conf file back to standard... then reinstallaed flgrx and everything is now fine...

Next issue - digital audio out... this is fun...

---

### Post by jonas80 on 2007-02-12
> **JonoMG said:**
> Whenever I attempt to play ANY type of media file X is crashing, I get jumbled colour splash screen (don't know if this is just X restarting or a symptom of the problem) and then I am presented with the login window.

When I say any media file, I mean any... I have tried Xvid, Vob, MP3, OGG. I have tried using Totem and VLC - both suffer the same fate. ](*,) *Update... I have tried playing some MP3's in Rhythmbox Music Player and no crash... don't know if that helps in the diagnosis.*

Sounds like you are using the fglrx drivers. I had the same problem with those drivers, music works as long as the player doesn't do any visualisation effects.

Try running mplayer with "mplayer -vo x11 video.mpg" and see if that works.

If that doesn't cause X to crash, and you are using fglrx drivers you can add **Option      "no_dri" "on"** to your device in /etc/X11/xorg.conf

Like this:

Section "Device"
[INDENT]Identifier  "aticonfig-Device[0]"
        Driver      "fglrx"
        Option      "VideoOverlay" "on"
        Option      "OpenGLOverlay" "off"
        **Option      "no_dri" "on"**[/INDENT]
EndSection

Hope this helps :) 

// Jonas

---

