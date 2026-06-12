---
title: "Looking for a media player that can do this..."
date: 2010-08-16
forum: Multimedia Software
---

### Post by Nostigex on 2010-08-16
I'm looking for a simple media player that can loop/repeat a given section of a song; say from 2:55 to 3:20 if I wanted. This would be useful for guitar practice.

Thanks

---

### Post by Nostigex on 2010-08-16
Bump.

---

### Post by cj.surrusco on 2010-08-16
You can do that with Audacity. It isn't a media player, it is a audio editor, but it will do what you want.

---

### Post by andrew.46 on 2010-08-17
Hi Nostigex,

> **Nostigex said:**
> I'm looking for a simple media player that can loop/repeat a given section of a song; say from 2:55 to 3:20 if I wanted. This would be useful for guitar practice.


MPlayer can do this:

```
mplayer -ss 00:02:55 -endpos 00:00:25 -loop 10 my_song.mp3
```

You can use *-loop 0* for infinite loop...

Andrew

---

### Post by Nostigex on 2010-08-19
Thanks andrew, that works, though it seems like a cumbersome approach to me. How would I do this in Audacity?

---

### Post by bigsmitty64 on 2010-08-19
In Audacity, with the file open, drag your mouse across the section you want to loop. Then go to "Transport"  in the top menu and click loop play!

---

### Post by mc4man on 2010-08-19
vlc player - use the 'loop from point a to point b continuously button'

(set point a, then when setting point b it  will start the loop - screen shows after setting

Edit:
unfortunately I don't believe the 'allow reading  EXTVLCOPT from saved bookmarks' will be patched into the maverick vlc.

If it was you could combine that with the loop function - save point a and point b to a .m3u as bookmarks, load the .m3u, pause the player and set the loop from the bookmarks - quite simple and would allow to quickly retrieve a specific loop for future use

Ex. this .m3u will set a loop from 20 - 40 secs
> #EXTM3U
#EXTINF:320,The Band - Tears Of Rage
#EXTVLCOPT:bookmarks={name=The Band - Tears Of Rage0,bytes=579791,time=20},{name=The Band - Tears Of Rage1,bytes=1161423,time=40}
file:///home/doug/Desktop/02%20-%20Tears%20Of%20Rage.mp3

---

### Post by kingheart on 2010-08-19
You can do it both in vlc and Audacity
IN VLC go to view>>show advanced control
then click loop from point A to point B. let your audio play. click it again.
your two points are selected. the audio will loop now!

---

### Post by Nostigex on 2010-08-19
Thanks guys! VLC is my favorite solution. Didn't know it could do that.

---

