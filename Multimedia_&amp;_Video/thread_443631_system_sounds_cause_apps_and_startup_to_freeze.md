---
title: "system sounds cause apps and startup to freeze"
date: 2007-05-14
forum: Multimedia &amp; Video
---

### Post by Faramir on 2007-05-14
I switched to Ubuntu about a week ago, and once I got my wireless card working, everything's been great, except for one problem. I have an ATI IXP AC97 sound card in a Compaq Presario R3000 laptop. My problem is that sometimes (apparently randomly) when a system sound such as the test sounds in the Sounds preferences panel plays, the application will freeze. I can force quit the application, but if I try to open it again it will not load and I'll have to force quit again. I've mainly encountered this problem in two places: the first is the Sound preferences menu. Once this freezes, several parts of GNOME will no longer function: the sound preferences panel, the shut down menu, and the terminal that I know of; however other applications, like Firefox, will still run normally.

The other place I encounter this problem is at startup. Sometimes when I log in, everything goes fine. However, the other times, a portion of the login music will play, then it will cut off and the panels will not appear. The wallpaper and mouse pointer will appear, but nothing else. Since there are no menus or buttons on the screen, I have no choice but to manually shut down the computer and try again. If it makes it through the entire login music without stopping, it always loads correctly; if the login music cuts off, it will not load correctly.

I have not encountered any problem playing audio CDs or audio files on the Internet. This problem only seems to be caused by system sounds. The sound card is recognized by Ubuntu: it shows up when I run
```
aplay -l
```
and works perfectly normally when playing other kinds of audio.

I suppose I could try just turning off all system sounds, but I'd rather find out what's causing this problem. I'd like to be able to start up my computer without having to cross my fingers that it will boot correctly, especially since Linux is renowned for its stability.

---

### Post by Faramir on 2007-05-14
Does anyone have any suggestions about this?

I also discovered that YouTube videos can cause Firefox to freeze. I don't know if this is related or not.

---

