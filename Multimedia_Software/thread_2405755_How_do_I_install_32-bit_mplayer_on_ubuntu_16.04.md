---
title: "How do I install 32-bit mplayer on ubuntu 16.04"
date: 2018-11-10
forum: Multimedia Software
---

### Post by edwardgibbon443 on 2018-11-10
Hi all,
I'm trying to play some "GMP4" format videos. I have the required **[COLOR=#FF0000]'GXAMP4.dll' [/COLOR]**in the codecs folder before configuring mplayer so I guess it should be in mplayer settings, but the video still won't play.
Some older post says that you need a 32-bit mplayer in order to play it, but I could not find a way of installing a 32-bit mplayer on ubuntu 16.04. I tried an old i386 deb file but it requires whole lot of i386 dependencies that I could not find.
Is there an easy way of installing a 32-bit mplayer on ubuntu 16.04?
Thanks:)

---

### Post by mc4man on 2018-11-10
Would be very problematic. While you can co-install many  amd64 & i386 libraries not all can be.

So mplayer .debs would depend on  libsmbclient. libsmbclient:i386 can't co-exist with the 64 bit version. To see run this, look at how many things are removed. (would be a bad thing to actually do..

```
sudo apt -s install libsmbclient:i386
```

---

### Post by SeijiSensei on 2018-11-11
If it's that important, you could use Virtualbox or some other virtualization software to install a 32-bit Ubuntu inside the 64-bit version.

---

