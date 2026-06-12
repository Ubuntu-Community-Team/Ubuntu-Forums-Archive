---
title: "Finally got RealPlayer working, but colors are off/inverted"
date: 2008-05-04
forum: Multimedia Software
---

### Post by AndrewZorn on 2008-05-04
Everything seems fine after my 10+ attempts at installing RealPlayer, but I must have done something wrong.  Perhaps I have some crazy codec or something that is taking over.  When I watch a video in RealPlayer, the colors are [almost] inverted.  I cannot find any setting that would be doing this.  Has anyone else had this problem?

EDIT xine, which I was only able to get by installing KDE, plays in the correct colors: but the audio is garbled, something I worked hard to fix.

---

### Post by BLTicklemonster on 2008-06-30
I finally got dvds to play by removing libdvdcss2 and getting the medibuntu repositories, and installing libdvdcss2 again, but now my colors are all messed up, too. almost like they are negative, but they aren't. Did a screenshot and opened it in gimp and inverted the colors just to be sure.

No idea how this can be fixed. Meanwhile the family sits back and laughs at the old man... Lovely.

---

### Post by AndrewZorn on 2008-06-30
Look for color settings or something, whether it's in mplayer or whatever I have no idea... the Hue by default is all the way to the wrong side after installing some crazy codec.

---

### Post by BLTicklemonster on 2008-06-30
Every player BUT mplayer would play the dvd with the hue wrong. Mplayer still has the same error for some reason. No other player has anything to change color settings from what I can see, so I installed kaffeine from the terminal, and it has it, and the colors are fine now.

Thank you.

---

### Post by orthopod on 2008-07-06
My colors in or hue in totem or mplayer movies in firefox were all shifted to green and purple.  I fixed it by adjusting with gxvattr

---

### Post by BLTicklemonster on 2008-07-26
A great guide:

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by jverville on 2008-08-16
This is what worked for me.  I am runny 32bit Hardy Heron.

Disable Xvideo inside RealPlayer. To disable Xvideo, click on the Tools menu in RealPlayer, click on Preferences and in the resulting options pane, select the Hardware tab and uncheck "Use Xvideo". Click "Ok" and restart the player. 

Realplayer displays the proper colors when playing a video now.

---

### Post by 1/0 on 2008-09-14
> **jverville said:**
> This is what worked for me.  I am runny 32bit Hardy Heron.

Disable Xvideo inside RealPlayer. To disable Xvideo, click on the Tools menu in RealPlayer, click on Preferences and in the resulting options pane, select the Hardware tab and uncheck "Use Xvideo". Click "Ok" and restart the player. 

Realplayer displays the proper colors when playing a video now.

Excellent! I've been looking for a way to set this once and for all so you don't have to issue: *xvattr -a XV_HUE -v 0* every time.

---

### Post by zorba_the_greek on 2008-10-24
> **jverville said:**
> This is what worked for me.  I am runny 32bit Hardy Heron.

Disable Xvideo inside RealPlayer. To disable Xvideo, click on the Tools menu in RealPlayer, click on Preferences and in the resulting options pane, select the Hardware tab and uncheck "Use Xvideo". Click "Ok" and restart the player. 

Realplayer displays the proper colors when playing a video now.

Thanks for that, but I am dealing with the same problem in Kaffeine and Totem, too. Do you have a solution for this??? :(:(

---

