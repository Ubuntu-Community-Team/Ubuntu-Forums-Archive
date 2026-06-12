---
title: "Config Mythvideo breaks Mythmusic"
date: 2008-08-25
forum: Mythbuntu
---

### Post by volkswagner on 2008-08-25
Well I am still running Mythbuntu 7.10, mythtv .21.

While trying get .avi vids to play, I had to edit the player settings in mythvideo. Using the default setting would play the audio track and lockup X.  I had to do reboot to get control.  Trying to restart gdm would continue audio playing.

Default
```
 mplayer -fs -zoom -quiet -vo xv -playlist %s
```

Research led me to make the x11 change from xv.

```
 mplayer -fs -zoom -quiet -vo x11 -playlist %s
```

This would let the vids play fine, but breaks sound in analog media.  Live digital tv=OK, live analog tv=NG, none of my .flac or .mp3 music plays.

Is this a bug?
What would be the best solution? 

edit:  I tried Xine.  Xine does not seem to break anything, but the remote buttons are not the same, ie:  I have to hit "q" to escapte or quit.  :( 

Master Backend/Frontend:
Mobo= GIGABYTE GA-MA69GM-S2H AM2 AMD 690G 
using SPDIf optical out for all sound
using svid out to SD TV

Looking through logs there are no errors, and mythmusic shows progress for music playing, just no sound.

---

