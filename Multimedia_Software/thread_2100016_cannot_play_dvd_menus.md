---
title: "cannot play dvd menus"
date: 2012-12-31
forum: Multimedia Software
---

### Post by leunam12 on 2012-12-31
Hi, I cannot play dvds menus in Lubuntu 12.10, I have tried Totem, mplayer, and VLC without success. I have searched extensively and all I have found have to do with the installation of libdvdread4 and libdvdcss and gstreamer bad and ugly plugins which I have. I can play the DVD without problem, what I cannot play is the menus. most programs crash when I try to play with menus.

I have no problem whatsoever in windows.

Any help ?

Thanks

---

### Post by andrew.46 on 2012-12-31
Have a look with SMPlayer and make sure you have enabled DVD menu playback, I attach a screenshot showing the relevant option. It is marked as experimental but I have rarely had trouble with this option.

---

### Post by leunam12 on 2013-01-01
Perfect, thank you.

----------------

ps: I like your signature

---

### Post by andrew.46 on 2013-01-01
> **leunam12 said:**
> Perfect, thank you.

Glad it worked for you :)

>  ps: I like your signature

From my favourite movie of all time...

---

### Post by leunam12 on 2013-01-01
I am a big Matrix fan also. I have watched so many times I think I know all the dialogs.

---

### Post by BubbaBlues on 2013-01-18
There is a problem with the latest version of libdvdnav4. Any dvd you copy with k9copy
or dvd95 with a menu will not play on the computer or a home dvd player.  They just choke when trying to read the menu.  
libdvdnav is a DVD navigation library, which provides an interface to the
advanced features of DVDs, like menus and navigation. It contains the VM and
other parts useful for writing DVD players. It's based on Ogle, but was
modified to be used by xine and mplayer.
They used to play perfectly before  4.2.0+201...
 Is there a way to change that file with an earlier version?

---

