---
title: "DVD Playback issues"
date: 2010-11-18
forum: Multimedia Software
---

### Post by Hawk666 on 2010-11-18
This has been an ongoing problem for me, when I insert a normal off the self DVD movie, I am unable to play it, I have tried 3 different media players:
Movie Player (An error occurred, could not read from resource)
VLC (loads the disc, shows a time of 00:00, and just won't play) GNOME MPlayer (pretty much the same as VLC, loads but won't play)

The funny thing about all this is that the one burned DVD I tried (no menus but structured as a DVD) will play, I'm thinking copyright?

---

### Post by efflandt on 2010-11-18
Did you install ubuntu-restricted-extras

and do [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

---

### Post by mc4man on 2010-11-18
Is libdvdcss2 installed? 
If not then an easy way to install is run this in a terminal
```
sudo /usr/share/doc/libdvdread4/install-css.sh
```

---

### Post by Hawk666 on 2010-11-18
yes i had installed ubuntu-restricted-extras, and i just tried to run through the process to set the region code and unfortunately I am still unable to play DVDs, VLC is now giving me the following error:

Playback failure:
VLC cannot set the DVD's title. It possibly cannot decrypt the entire disc.
Your input can't be opened:
VLC is unable to open the MRL 'dvd:///dev/sr0'. Check the log for details.

the other 2 media players are still doing the same thing, I also get the same error in VLC is I open without menus

---

### Post by Hawk666 on 2010-11-18
solved, thanks guys, im so used to NOT rebooting with ubuntu that i didnt think to, all is working now

---

### Post by mc4man on 2010-11-18
> im so used to NOT rebooting with ubuntu
Yeah, I keep forgetting to suggest that, starting in karmic and up rebooting seems to have become a possible solution when adding/removing codecs/plugins ect.

---

