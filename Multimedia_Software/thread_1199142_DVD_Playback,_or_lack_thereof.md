---
title: "DVD Playback, or lack thereof"
date: 2009-06-28
forum: Multimedia Software
---

### Post by AlexGrim on 2009-06-28
Hey guys, i am actually a Fedora User, and know very little about Ubuntu. I install Ubuntu on computers for newer computer users, because i think it is the best distro for them.

I was trying to get the dvd playback to work on one of these computers, but cannot seem to get it. I have libdvdnav4 and libdvdread4 installed, but vlc, mplayer, and the other players still will not play a dvd. Is there something that i am missing?

I know that with Fedora, you have to install libdvdcss, but i cannot find that for Ubuntu. Is this even necessary?

Thanx

---

### Post by HotShotDJ on 2009-06-28
Yes.  You need libdvdcss.  But it is not included in the repositories for legal reasons.

There are two ways to deal with it.  The easiest is to install the [Medibuntu]("https://help.ubuntu.com/community/Medibuntu") repositories and install libdvdcss from there.

If you have libdvdread4 installed, you can also run the following from a terminal:```
sudo /usr/share/doc/libdvdread4/install-css.sh
```

---

