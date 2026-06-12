---
title: "Myth Video + X11 Screen Number"
date: 2008-01-27
forum: Mythbuntu
---

### Post by ian dobson on 2008-01-27
Hi,

Due to various reasons I'm running my MythTV frontend with 2 Displays (Screen 0 17' LCD and Screen 1 TV PAL output over S-Video).

I can change the screen number that Mythfrontend uses to use my TV but when I try and use Myth Video to look at old AVI's of the family the video plays on screen 0 (LCD).

Is there a way to force the player to use a different screen. I've seen that there is an option in Myth frontend to configue how mplayer is called but no matter how hard I look I can't find an option for the screen number.


Regards
Ian Dobson

---

### Post by ian dobson on 2008-01-28
OK, problem solved.

I ended up manually editing xorg.conf so that the TV is screen 0 and the LCD is screen 1.

 By default the screens are the over way round which worked for me as long as the LCD was attached. But as soon as I disconnected the LCD the display configuration went mad and TV pnly displayed part of the Myth frontend.

Regards
Ian Dobson

---

