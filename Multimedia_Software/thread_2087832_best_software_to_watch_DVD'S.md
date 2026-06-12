---
title: "best software to watch DVD'S"
date: 2012-11-24
forum: Multimedia Software
---

### Post by trixman on 2012-11-24
looking for the best linux software to play my DVD's in ?

:popcorn:

---

### Post by robbie 348 on 2012-11-24
VLC works best for me.

---

### Post by kherring7383 on 2012-11-24
I have to totally agree, VLC is a good choice. But if you want to check out another good player, SMPlayer at [http://smplayer.sourceforge.net/](http://smplayer.sourceforge.net/)

---

### Post by Futant on 2012-11-24
Another vote for VLC from me... Make sure you have the restricted extras installed...

---

### Post by evilsoup on 2012-11-24
Just remember that you have to install libdvdcss2 to watch most commercial DVDs, though I think it's part of ubuntu-restricted-extras so you probably already have it. With that, pretty much any media player will work perfectly well.

That said, VLC.

---

### Post by monkeybrain2012 on 2012-11-24
vlc for DVDs, Smplayer (with mplayer2 as backend) for local movie files since it doesn't support DVD menu (if that is important for you)

Totem is ok too for DVD quality.

---

### Post by andrew.46 on 2012-11-25
I think you could toss up between vlc and SMPlayer for dvd playback. Mind you a better alternative is a big screen television :)

---

### Post by trixman on 2012-11-25
i went with the VLC

it seems to play great. just looking to play some old cartoons and stuff.

thanks:P

---

### Post by col48 on 2013-02-13
*_following up post #5 re libdvdcss2._*

libdvdcss (with or without the '2') is not listed in Synaptic (Lucid 10.04, anyway) so having installed vlc, ubuntu-restricted-extras and libdvdread4  I found I needed to follow the instruction on

[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

Quoting from there, in a terminal....

sudo /usr/share/doc/libdvdread4/install-css.sh

This was the only ingredient I lacked to have vlc successfully read commercial dvds.  I did not have to reboot, just restart vlc.

---

